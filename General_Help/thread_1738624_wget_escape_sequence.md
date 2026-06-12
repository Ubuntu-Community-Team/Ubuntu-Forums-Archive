---
title: "wget escape sequence"
date: 2011-04-25
forum: General Help
---

### Post by myaces on 2011-04-25
I'm trying to parse some redfin pages and it seems like I'm having a problem with the # symbol.

Running the following:

echo 'http://www.redfin.com/homes-for-sale#!search_location=issaquah,wa&max_price=275000' > /tmp/issaquah_main.txt
wget --level=1 -convert-links --page-requisites -o issaquah/main -i /tmp/issaquah_main.txt

I error out at the # symbol but I can't seem to escape it, any ideas?

---

### Post by myaces on 2011-04-25
Any ideas?  This is the message, as you can see the # has been removed.

--2011-04-25 21:27:48--  [http://www.redfin.com/%5C%22http:%5C/%5C/img.cdn-redfin.com%5C/v6.2.5%5C/images%5C/logos%5C/gamls.png%5C%22](http://www.redfin.com/%5C%22http:%5C/%5C/img.cdn-redfin.com%5C/v6.2.5%5C/images%5C/logos%5C/gamls.png%5C%22)
Connecting to [www.redfin.com|98.142.98.97|:80](www.redfin.com|98.142.98.97|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-04-25 21:27:48 ERROR 404: Not Found.

---

### Post by The_Tim on 2011-04-26
Hi, myaces, Tim Ellis from Redfin here.

We're certainly flattered that you love our data, but we can't support [scraping]("http://en.wikipedia.org/wiki/Web_scraping") (which it appears you're trying to do here).  Scraping is poor internet etiquette in general, and our contracts with the MLSes (the listing services that supply us with home listing data) compel us to take whatever measures we can to prevent scraping.  It is also explicitly disallowed in our [Terms of Use]("http://www.redfin.com/stingray/do/terms-of-use#5._Webscraping_of_Listing_&_Property_Data_Is_Not_Allowed").

We wish you the best of luck in your venture, but please find another way to get the data you need that does not involve scraping it from our site.

---

### Post by myaces on 2011-04-27
Hey Tim, thanks for the reply!  Might I suggest adding CAP rates, IRR, MIRR and Cash Flow to your website for investment properties?  Then I'd have no need to scrape!

:)

---

