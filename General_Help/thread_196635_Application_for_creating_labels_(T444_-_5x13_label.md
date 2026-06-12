---
title: "Application for creating labels (T444 - 5x13 labels per page)"
date: 2006-06-14
forum: General Help
---

### Post by daller on 2006-06-14
Hi there,

I work in a local techshop, and want to make label-printing easy.

(We use labels for name, price, and number)

Our present solution is an openoffice-document with a table in it! - It works well, but I would like an application for it!

The reasons why I would prefer a label-application:

* Easy creation of several labels.
* Maybe a database-function, for even easier management. - Selecting catalognumber, and number of labels, etc...

Any suggestions?

---

### Post by The Mekon on 2006-06-14
Look at gLabels.  It has a wide range of predefined labels and you can also create your own templates.

---

### Post by daller on 2006-06-16
It doesn't seem to have a database-function...

I'll go for some home-created php-script... (though it'll take a while...)

fpdf is great! (a php module!)

Thanks for the tip, though!

---

### Post by bdalzell on 2006-08-06
gLabels accepts as a datasource a spreadsheet in various formats such as csv, colon separated, tab separated, etc. You point it to the spreadsheet using the Objects>merge properties option and at that time you tell it what sort of spreadsheet you have.

If you are trying to make labels from part of a database you can go into your database program, select the items you need to make into labels and save those selections out (ie export them) into a spreadsheet. gLabels will then make your Labels from the spreadsheet.

If you need more than one label for each item, but not the same number of multiple labels between items, a quick way to do this is just to duplicate the item in the spreadsheet as many times as you need it.

---

