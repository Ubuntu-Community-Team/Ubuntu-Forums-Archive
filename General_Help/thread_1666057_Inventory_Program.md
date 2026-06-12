---
title: "Inventory Program?"
date: 2011-01-13
forum: General Help
---

### Post by luxsphinx on 2011-01-13
I'm an electronics hobbyist with a lot of parts that I would like to keep track of in terms of amount.  Up until now, I have simply kept a list of the various parts in a spreadsheet with the second column being the quantity left.  After using parts, I would go through the list and deduct from the quantities accordingly.  However, I have a USB barcode scanner and have given the different electronic components that their own barcode.  I'm looking for a simple inventory program that would allow me to just scan the barcode to deduct one from the quantity and have an option to scan the code to add to the quantity (when I buy more of the parts).

Does anyone know of any Ubuntu programs that would fit this purpose?

Thanks,
Lux

---

### Post by ronnielsen1 on 2011-01-13
[http://linux.softpedia.com/progDownload/Inventory-Management-Software-Download-2821.html](http://linux.softpedia.com/progDownload/Inventory-Management-Software-Download-2821.html)

[http://www.openerp.com/downloads](http://www.openerp.com/downloads)

[http://www.sql-ledger.com/](http://www.sql-ledger.com/)

[http://tellico-project.org/](http://tellico-project.org/)

See if any of these fit your needs

---

### Post by luxsphinx on 2011-01-13
> **ronnielsen1 said:**
> [http://linux.softpedia.com/progDownload/Inventory-Management-Software-Download-2821.html](http://linux.softpedia.com/progDownload/Inventory-Management-Software-Download-2821.html)

[http://www.openerp.com/downloads](http://www.openerp.com/downloads)

[http://www.sql-ledger.com/](http://www.sql-ledger.com/)

[http://tellico-project.org/](http://tellico-project.org/)

See if any of these fit your needs


Thanks! I'll take a look and try them out.

---

### Post by luxsphinx on 2011-01-14
I ended up going the route of PHP and database accessed via the browser.  I'm posting back in case someone else might benefit from a similar set up.  After trying out Tellico, DataCrow (which I already use for books, music, and movies), PHP Inventory, and PHP Point Of Sale, I've found that PHP POS works the best for my needs.  It can be found over at [URL="http://www.phppointofsale.com/"]http://www.phppointofsale.com/
[/URL]
I set up a database for it and can now do exactly as I wanted and more.  Not only does it allow me to scan barcodes and then have that amount deducted from the overall inventory.  Since it is essentially a store checkout system, it'll even ring up the total cost of the parts with tax included (useful to know just how much a project cost), notify me of low inventory, keep track of all the stores I buy parts from, and give me a receipt after the project that I can file as a parts list if I ever want to build another.  PHP Inventory was a runner up, but just wasn't as functional and the others simply were too much of a hassle to create custom collections of parts - they were designed for a growing collection, not one that is constantly going up and down with multiples of items.

Thanks so much for the offering up some options!

---

