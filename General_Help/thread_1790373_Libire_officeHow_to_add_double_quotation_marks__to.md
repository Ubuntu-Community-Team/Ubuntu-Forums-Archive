---
title: "Libire office:How to add double quotation marks  to contents of an column quickly"
date: 2011-06-24
forum: General Help
---

### Post by huangweiqiu on 2011-06-24
I want to add double quotation marks to contents of an column ,the column contains over 7000 cells with content already,so it would be heavy task to add "double quotation marks"one by one.Is there any way to do that quickly on Libre office?

Thanks in advance.

---

### Post by gmargo on 2011-06-25
I assume you are speaking about LibreOffice Calc - the spreadsheet.

Fairly simple to do in Calc:


[LIST]
[*]Select entire column.
[*]Pull up the Find & Replace dialog (Edit -> Find & Replace)
[*]Click the "More Options" button on the dialog.
[*]Enable the "Regular expressions" checkbox.
[*]In the "Search for" field put this:
    (.*)
[*]In the "Replace with" field put this:
    "$1"
[*]Click the "Replace All" button.
[/LIST]

---

