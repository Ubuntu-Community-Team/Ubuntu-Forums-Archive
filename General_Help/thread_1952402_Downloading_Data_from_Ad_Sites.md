---
title: "Downloading Data from Ad Sites"
date: 2012-04-04
forum: General Help
---

### Post by Aqil on 2012-04-04
I've been looking into downloading data from ad sites such as eBay and Craigslist.

Let's say I want to investigate the correlation between price, milage and year manufactured for all Ford Taurus. It could be stamps or whatever. This information is easily found on many sites in standardized format, but writing all of it down manually would be immensely time consuming.

What is the best approach to do this? I've been reading some about data mining and web crawling, but I'm still a bit confused as to what software I should use. I don't need any analysis functions in addition to what I already have. I would love a minimalitic program with GUI that enables me to download large amounts of data, perhaps in Excel or .csv format. Is it possible?

Thanks!

---

### Post by Bill Z on 2012-04-04
Perl is a programming language designed for that.  It will allow you to scrape information from web pages.

If you are even somewhat interested in learning Perl, you can get a  Perl for dummies as a starting place.  This and other books are available on the net.

---

### Post by raja.genupula on 2012-04-04
> **Bill Z said:**
> Perl is a programming language designed for that.  It will allow you to scrape information from web pages.

If you are even somewhat interested in learning Perl, you can get a  Perl for dummies as a starting place.  This and other books are available on the net.

and some more 
[http://ubuntuforums.org/showpost.php?p=2020378](http://ubuntuforums.org/showpost.php?p=2020378)

---

### Post by Aqil on 2012-04-04
I don't doubt that Perl is great. But I'm not a programmer and I don't plan on becoming one, so I'm afraid I can't put in enough time into learning an entire programming language and make a new program from scratch. I don't mind writing some simple IF ELSE commands or rules, but I do mind spending months learning computer science before I can even start analyzing. Isn't there any simpler way to do it?

---

### Post by dragonfly41 on 2012-04-04
For web mining you might find the built in web spyder in TextSTAT tool useful

[http://www.niederlandistik.fu-berlin.de/textstat/](http://www.niederlandistik.fu-berlin.de/textstat/)

I copied TextSTAT into /home/myusername/Applications/TextSTAT   ... but it can be placed anywhere

then launch using command

cd /home/myusername/Applications/TextSTAT/    &&  python TextSTAT.pyw

build a corpus of the web sites you need to trawl

you can search concordance for key phrases

For other web mining tools look here .. [http://www.kdnuggets.com/](http://www.kdnuggets.com/)

and here .. [http://semanticweb.org/](http://semanticweb.org/)


[Edit]

p.s. .. also you might try pipes .. [http://pipes.yahoo.com/pipes/search?r=source%3Acolumbia.craigslist.org](http://pipes.yahoo.com/pipes/search?r=source%3Acolumbia.craigslist.org)

---

### Post by Aqil on 2012-04-04
dragonfly41,

Thank You for your imput! I will definitely look into these ideas further.

---

### Post by SeijiSensei on 2012-04-04
If the data you need to import are in HTML tables on a web page, you can highlight the table with the cursor in your browser, choose copy, then paste the data into a spreadsheet.  This works with gnumeric, OO/LO Calc, and MS Excel.  All of them know how to translate from the <TR> and <TD> row and cell delimiters in HTML into spreadsheet rows and columns.

---

### Post by Aqil on 2012-04-04
SeijiSensei,

Usually each row of data is on an individual page and this is what makes the collection of a complete sample so onerous. Thanks anyway!

---

### Post by SeijiSensei on 2012-04-04
I was thinking more of pages like Google Shopping generates, but the data there are layed out using <div>'s rather than an HTML table.  I tried importing a page of results from them, but it didn't import correctly into LO Calc.  I didn't try any other spreadsheet programs to see if they fare better.

---

### Post by dragonfly41 on 2012-04-05
I know that OP was not keen on Perl scripting but perhaps consider PHP if the above lists to mining tools don't work out. 
 The mining tools are more for unstructured text than mining data in tables (which can more simply be parsed by DOM).

Install PHP5 (or LAMP server)

try [http://simplehtmldom.sourceforge.net/](http://simplehtmldom.sourceforge.net/)

and parse for elements 

Or try PHP cURL extension

...

Alternatively .. returning to earlier idea about using yahoo pipes .. here is one example

[http://pipes.yahoo.com/pipes/pipe.info?_id=oibdg__42xGtJOXN1vC6Jw](http://pipes.yahoo.com/pipes/pipe.info?_id=oibdg__42xGtJOXN1vC6Jw)

view source and amend to your requirements.

---

### Post by Aqil on 2012-04-07
Well, if the data is neatly arranged in table or text format on a single URL it's easy peasy to copy, paste and reformat or transform. The challenge is to download data from sites where data is dispersed throughout many pages and one has to click each link to get all info.

---

### Post by dragonfly41 on 2012-04-08
I'm not sure what is the challenge ..

if using PHP script you scrape each site using cURL or simplehtmldom

you parse the content (elements) you want and any links you parse and use as a vars (target pages) in your next cURL search.

If you point to an example of a problem page(s) to scrape this might make answers easier.

---

### Post by Aqil on 2012-04-08
The challenge is to get an English translation of what you're saying. I don't know what scrape, cURL and simplehtmldom is. How would you explain it to your grandmother? Is there a point and click version?
 
Take[ this site]("http://www.gumtree.com/property-for-sale") for example, with over 200,000 property for sale ads all over the UK on over 4,000 pages. In order to get all the available info, you must click your way through each and every ad. In this case you can get the following standardized variables
 
Price:
Property type:
Number of beds:
Seller type:
 
and perhaps also, phone number, location, time and date, and more.
 
The challenge is to do this as easily and quickly as possible.

---

### Post by dragonfly41 on 2012-04-08
This tutorial will help you to understand the basics of web scraping .. but beware that you might be blacklisted if you breach a site's policy (you've now given gumtree as your example but previously it was craigslist and eBay..

[http://www.codediesel.com/php/web-scraping-in-php-tutorial/](http://www.codediesel.com/php/web-scraping-in-php-tutorial/)

If this is out of your depth then 

[http://stackoverflow.com/questions/1169774/how-do-you-install-simplehtmldom-in-ubuntu](http://stackoverflow.com/questions/1169774/how-do-you-install-simplehtmldom-in-ubuntu)

and possibly [http://www.w3schools.com](http://www.w3schools.com) to understand DOM.

To understand the DOM (layout) of any target page you'll find Firebug useful as Firefox add on.

[http://getfirebug.com/](http://getfirebug.com/)

Right click on any item in your property list and select "Inspect Element with Firebug".  Then use this structure to write .. yes write .. your script.

[later edit]

I'm adding this link to a Firefox addon which you might try out (free version restricted to 100 items)

[http://www.outwit.com/products/hub/](http://www.outwit.com/products/hub/)

it comes from here .. [http://www.timedicer.co.uk/web-scraping](http://www.timedicer.co.uk/web-scraping)

---

### Post by Aqil on 2012-04-08
This seems to be great resources. I will study it in more detail before I perhaps get back to ya'all with follow up questions. Thank You dragonfly41 for your patience, time and effort! I don't know what I would do without goodhearted and knowledgable people like you.

---

