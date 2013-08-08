JSInvoicingSystem
=================

# Overview
In my search for a decent way to make invoices for my small web company, I was faced with 2 options:

* Use an OS specific system for invoicing
* Use a webbased system

The first was a No Go since I'm a native Linux User, but in the future another person in the company might use another OS. The second Option seemed the way to go, but there was nothing decent out there. 

* You either pay for the software
* Or the UX is even worse than the crappy UI
* On top of that, you always need a server. So on the plane, there is no way to do your invoices

**Solution:** Go fix it yourself.

And so this project started: A client-side JS only way of making invoices, getting stock counts, and have some kind of user management. All packaged in a beautiful Chrome WebApp. (In the future I might add a firefoxOS version.)

# Breakdown
At the moment, their isn't anything more than an idea and some pieces of the puzzle filled in. The project will consist of:

* A javascript framework (Barebone?)
* An Initializr front-end
* An Invoice templating system
* A javascript based PDF creator

# Working backwards
There are only two 2 pieces which are not as straightforward as I'd like:

1. Data storage in the App. (SQL databases are no option in offline mode)
2. Getting the data in a PDF that isn't cripple

Because I fear the second one most, I decided to start with that. The original idea was to use an SVG file, modify it according to the invoice you want, and then export that as a PDF. It's easy in inkscape or via terminal, but not that easy via Javascript. I tried all of them, jsPDF was one of the better ones, but it's not easy to "template" with it. It's not dummy friendly.

So I just modify an existing PDF for now. The pdf just substitutes tags from the original pdf with new ones, and does some basic mathematical magic to get the offset for multiple products. **I know this method is dirty as hell, and I would love to have another way to do this. So anybody who knows a better way, please contact me!**

*Note: A lot of PDF files don't have the text clearly written. They use filters with algorithms (like the gZip algorithm) to make the text smaller (hence: that's why your pdf is 20kb and your .doc is 250kb). Since I'm not planning on decrypting those in the first version of the app, you have to provide a clear text PDF. I'll include a way to "decrypt" a PDF once I've got something that actually works (kinda)*

# ToDo
## PDF exporter

* Make a template file
* Find a javascript alternative that does what sed does in commandline (regex)
* Make it look for tags and change the customer info etc.
* Make a math algorithm for the positioning of extra products.
* Find a beautiful way to include new pages.

## Frontend
* Find a designer, give him carte-blanche.
* Do tell him that invoicing should be primary, and visible from the "home screen".

## Backend
* Write a customer & product management backend with data models in backbone
* Figure out how to use the localStorage (or alternatives) in a ChromeApp
