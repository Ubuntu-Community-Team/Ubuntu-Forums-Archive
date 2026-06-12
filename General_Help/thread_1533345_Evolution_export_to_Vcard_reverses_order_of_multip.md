---
title: "Evolution export to Vcard reverses order of multiple address lines"
date: 2010-07-17
forum: General Help
---

### Post by jwood1961 on 2010-07-17
Using Ubuntu Lucid Netbook edition with all latest updates applied. Evolution 2.28.3.

Export an addressbook to Vcard (in this case many contacts to one file) and if the contact contains more than one line in "address", these lines appear in the same order as entered for the LABEL entry in the VCARD, but are given in reverse order in the actual ADR field.

Thus, importing the Vcard into another application (eg: Gmail contacts) what was entered in Evolution as, say:

PO Box 333
12 Somewhere Drive
Some District
Some City
Some State
Zip
Country

becomes

PO Box 333
Some District
12 Somewhere Drive
Some City
Some State
Zip
Country

when imported to or viewed in any other aplication, except Evolution where the reversal is reversed on re-importation.

And in fact the PO Box field is exported into the LABEL in-between the Zip-code and the country, (not at the start of the label where it should be).

Surely aberrant behaviour which does not follow the Vcard spec?
JW

---

