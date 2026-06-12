---
title: "Repeat rows in Open Office 3.2 Calc"
date: 2010-10-28
forum: General Help
---

### Post by saskatchewan on 2010-10-28
I have been trying to repeat the first two rows in a Calc document but I keep getting an error.

Here are the instructions that I used.

Printing Rows or Columns on Every Page 
If you have a sheet that is so large that it will be printed multiple pages, you can set up rows or columns to repeat on each printed page.
As an example, If you want to print the top two rows of the sheet as well as the first column (A)on all pages, do the following:
1.Choose Format - Print Ranges - Edit. The Edit Print Ranges dialog appears.
2.Click the icon at the far right of the Rows to repeat area.
The dialog shrinks so that you can see more of the sheet.
3.Select the first two rows and, for this example, click cell A1 and drag to A2.
In the shrunk dialog you will see $1:$2. Rows 1 and 2 are now rows to repeat.
4.Click the icon at the far right of the Rows to repeat area. The dialog is restored again.
5.If you also want column A as a column to repeat, click the icon at the far right of the Columns to repeat area.
6.Click column A (not in the column header).
7.Click the icon again at the far right of the Columns to repeat area.

Rows to repeat are rows from the sheet. You can define headers and footers to be printed on each print page independently of this in Format - Page.


And here is the error.

"invalid sheet reference"

---

### Post by JerreCope on 2011-03-08
See [https://bugs.launchpad.net/openoffice-pkgs/+bug/374708](https://bugs.launchpad.net/openoffice-pkgs/+bug/374708) #26

To quote:

1.From the menu, go to Tools->Options->OpenOffice Calc->Formula
2. Click on the Formula syntax dropdown and select "Excel A1". Click it again and change it back to "Calc A1"
3 Click OK button.

---

