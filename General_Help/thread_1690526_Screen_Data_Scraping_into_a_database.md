---
title: "Screen Data Scraping into a database"
date: 2011-02-18
forum: General Help
---

### Post by chipchop on 2011-02-18
I use ubuntu lucid 10.4.  I would like to monitor stock prices in realtime with a web browser and generate spreadsheets.  Is there a program to scrape the data from the screen and put it into an openoffice spreadsheet so that I can categorize the data appropriately?  I would like to do this in realtime if possible.  Perhaps a firefox addon or chrome extension.  I have searched for this for a while and think I may have to write my own code, which would be okay, but I imagine that there is some open source code out there that would work or can be changed a little to suit my needs.  Please point me in the right direction.

---

### Post by oldfred on 2011-02-18
[http://www.goldb.org/ystockquote.html](http://www.goldb.org/ystockquote.html)

See also this if you can find it:
The Python Papers, Volume 2, Issue 4
Screen Scraping Web Pages

There are several python programs that either download the yahoo or google daily data (15 min delay), or daily  historical data. I also found but not saved links,  to several example o screen scraping data are in python.

[http://vermeulen.ca/python-stock-market.html](http://vermeulen.ca/python-stock-market.html)

I have tried updating one or two of the spreadsheets that do the same, but they were in excel and the basic required a lot of changes to work. 

Do a google search on  python stock quote

---

### Post by chipchop on 2011-02-18
Thank you for responding so quickly. That is exactly what I was finding, but nothing on the opensource front. I am a bit surprised that there isn't an opensource project for a page scraping program, especially with the interest lately on the penny auction front, which is another type of program I ran into while searching for the proper application for me to use.  I think it would be a useful to have a gui designed to parse data from any website into an openoffice spreadsheet, maybe I am alone in this.  Obviously, it would be cumbersome for the user to adapt it to a specific website (programming language, data placement), but it is rare when we (ubuntu users) do anything that is not a learning experience.  I imagine that the best way to do this would be as an add-on to one of the browsers.

---

### Post by oldfred on 2011-02-18
I found this, which is the same author and I think the same info in the Python Papers:

[http://www.goldb.org/pythonwebscraping.html](http://www.goldb.org/pythonwebscraping.html)

I have not tried BeautifulSoup or Scrapy which seem to come up in google.

I have always believed that the market makers are the only ones making money on penny stocks as the bid/ask spreads are so high.  And some are just scams to run up prices, they sell and you are left hanging.

---

