---
title: "mySql to php to html to web browser to html file to OpenOffice Writer fails on styles"
date: 2012-01-11
forum: General Help
---

### Post by desconocido on 2012-01-11
I have address book data from a Legacy application in csv format. I want to be able to update the data and also format it (font, font-size, bold, italic, indents, no-wrap) into multi-column formats so that I can print it out on special paper for Filofaxes.

So I imported it into mySQL, wrote some php to output html with a stylesheet and the format looks fine in browsers (Firefox and Opera) but does not, of course(?), handle the multi-column or page break requirements.

So I want to put the output into OpenOffice writer (version 3.2), into a file with the correct multi-columns. I tried cut and paste from the browser into Writer. I also tried saving the web page as an html file and using the Writer "Insert -> File..." command. In both cases, all the formatting is left out.

This appplies both to using an external stylesheet and to putting the styles into the <head> of the html. (I can get, e.g., bold to work by using old fashioned <b>..</b> attributes but I'm  not sure that all the things I do with the styles can be done thus.)

Are there any upgrades or extensions or plug-ins I could get to solve this problem? Or any workarounds? (I don't want to format the data by hand.) 

Or any alternative ways of getting from the csv data to Filofax sheets? (Filofax's own software didn't work for me.)

(Can css styles for print media help me with the multi-column requirement and let me print straight from the browser?)

Thanks.

---

### Post by gsgleason on 2012-01-11
Just a guess, but if you're working with tabular data, why try to use writer instead of calc?

---

### Post by desconocido on 2012-01-11
> **gsgleason said:**
> Just a guess, but if you're working with tabular data, why try to use writer instead of calc?

Not really tabular, I'm just trying to get three columns of this sort of stuff onto each paper page.

---

### Post by mbeach on 2012-01-11
I may not be following correctly, but if the goal is to print the data for labels, maybe you are looking to mail merge the data?

I would make the csv file your data source, and skip mysql/php step altogether (unless you are doing that for another reason other than to print).

See something like:
[http://openoffice.blogs.com/openoffice/2007/01/mail_merge_in_o.html](http://openoffice.blogs.com/openoffice/2007/01/mail_merge_in_o.html)

May get you in the right direction.

---

### Post by SeijiSensei on 2012-01-11
> So I imported it into mySQL, wrote some php to output html with a stylesheet and the format looks fine in browsers (Firefox and Opera) but does not, of course(?), handle the multi-column or page break requirements.

Have your PHP script write out the data as a three-column HTML table.  Something like this (untested): 

```

$ncolumns=3;
$result=mysql_query("select * ... ;");
$N=mysql_num_rows($result);

# begin the table
echo "<table width='100%'>\n<tr><td width='33%'>\n";

# determine where the columns should break for evenness
$break1=floor($N/$ncolumns);
$break2=2*$break1;
if ($N%3==1) { $break1++; }
if ($N%3==2) { $break2++; }

# iterate over the results
$i=0;
while ($row=mysql_fetch_assoc($result)) {
   echo $row['field'];
   # start a new column if at a break point
   if ($i==$break1 || $i==break2 ) { 
      echo "</td>\n<td width='33%'>\n";
   } else {
      echo "<br/">\n;
   }
   $i++;
}

# close the table
echo "</tr></table>\n";

```

This should display the results in three columns with as close to equal numbers of entries per column as possible.  (You may have to play with how $break1 and $break2 are determined.)

---

### Post by desconocido on 2012-01-11
> **mbeach said:**
> I may not be following correctly, but if the goal is to print the data for labels, maybe you are looking to mail merge the data?

I would make the csv file your data source, and skip mysql/php step altogether (unless you are doing that for another reason other than to print).

See something like:
[http://openoffice.blogs.com/openoffice/2007/01/mail_merge_in_o.html](http://openoffice.blogs.com/openoffice/2007/01/mail_merge_in_o.html)

That would work, but it's not for labels - I'm trying to cram as many records into each column and A4 page as possible, and your reference suggests that mail merge produces one page per record. With three columns per page, I'm looking to get between 8 and 12 records (varying numbers of lines of text) into each column. That's roughly 24 to 36 records per page.

---

### Post by desconocido on 2012-01-11
> **SeijiSensei said:**
> Have your PHP script write out the data as a three-column HTML table.  Something like this (untested): 

...snip...

This should display the results in three columns with as close to equal numbers of entries per column as possible.  (You may have to play with how $break1 and $break2 are determined.)

Yes, but - each record will turn into between 2 and say 10 lines of text, so I will want to fill the first column of the first page, then the second column, then the third column and then the first column of the second page etc. Not sure I know how to control page breaks in html.

The attached screenshot gives the flavour of a layout with just two columns: the coloured areas are where the text goes.

---

### Post by SeijiSensei on 2012-01-12
Page breaks are indeed difficult because HTML isn't designed for formatted pages.  I've used HTML tables to create "pages" by specifying the width and height of the box so it conforms to the paper on which it's being printed.  Still it's a pretty arduous task to make sure everything fits where it's supposed to.

---

### Post by desconocido on 2012-01-12
> **SeijiSensei said:**
> Page breaks are indeed difficult because HTML isn't designed for formatted pages.  I've used HTML tables to create "pages" by specifying the width and height of the box so it conforms to the paper on which it's being printed.  Still it's a pretty arduous task to make sure everything fits where it's supposed to.

Yes, maybe the newish print css options (as described for example in
[http://www.transmissionzero.co.uk/computing/css-for-printing/](http://www.transmissionzero.co.uk/computing/css-for-printing/)
might help, especially the bit on page breaks.

I presume you could define a css id such as
```
#last-piece-on-the-page
{
  page-break-after: always;
}
```

and I could write php code to associate the id with the last span or div that would fit on the page, and I could combine that with your column code. Would just need to sort out my custom margins.

---

### Post by desconocido on 2012-01-14
OK, I have something now that I can live with:
Show the data in the web browser, save as .html
Open the .html file directly in OpenOffice Writer 3.2
Go to "Format -> Page" and set the Margins, number of columns, column widths, column spacing.
Manually look at each column and insert a column break if necessary to keep data together in one column and to start new letter on new column.

Just wish there was a one-click column break.
Thanks for the help.

---

