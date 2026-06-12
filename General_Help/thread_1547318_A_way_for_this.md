---
title: "A way for this :?"
date: 2010-08-06
forum: General Help
---

### Post by Fxy on 2010-08-06
Hello all

Me & a friend of mine both have ubuntu 10.4 installed on our laptops & have been looking into accomplishing various different tasks.  One of those tasks we are currently stuck upon & thought of turning here for all open suggestions ;-)

Well as it goes what we are looking to do is to have our laptop/s connect to the internet then automatically search & download image / videos with a certain name...

Is there any way we can accomplish this, instead of having to search the web manually :?



Any suggestions & comments welcome :-)

---

### Post by rhigmus on 2010-08-06
interesting idea. don't know about getting images automatically w/ keywords. but theres a program called TED ([torrent episode downloader]("http://www.ted.nu/download.php")) that will auto download .torrent files of television shows. it even has a database of current programs you can choose from.

---

### Post by endotherm on 2010-08-06
you can definetly do it, but it will be problematic to maintain. the general idea is to send a request to the search service, and recieve its resultset as an html document. then your app would read the html, extract the peices it wants, and then acts on them.

the problem is that parsing kinda requires the document content to be predictable, and sites change their code all the time.

I use a secure frontend for google called [Scroogle]("https://ssl.scroogle.org/cgi-bin/nbbwssl.cgi"). it's a great service, but everytime google changes the layout of the page that they scrape to parse out the results, scroogle goes down until the old layout is available again, or the scroogle devs update their code (something they are reluctant to do, as it does open the floodgates).

---

### Post by corrytonapple on 2010-08-06
10.4 is in beta and is not supported very well here. 10.04 is the current stable release. Do you mean 10.04?

---

### Post by endotherm on 2010-08-06
> **rhigmus said:**
> interesting idea. don't know about getting images automatically w/ keywords. but theres a program called TED ([torrent episode downloader]("http://www.ted.nu/download.php")) that will auto download .torrent files of television shows. it even has a database of current programs you can choose from.
wrote a python script to do this for manga viewer sites. pull the page, parse out the links, download the content, ride the "next" link to the next page, and do it all over again.

---

### Post by WorMzy on 2010-08-06
> **corrytonapple said:**
> 10.4 is in beta and is not supported very well here. 10.04 is the current stable release. Do you mean 10.04?

10.04/10.4 are the same thing; the numbers in Ubuntu's releases just signify the date it was released: 10 is the year (2010), 4 is the month (April).

You could probably cobble something together with bash scripts and wget, but I don't know of any specific tools for this sort of automated activity. You could use something like [DownloadThemAll!]("http://www.downthemall.net/") to pick things up as your surf.

---

### Post by corrytonapple on 2010-08-06
> **WorMzy said:**
> 10.04/10.4 are the same thing; the numbers in Ubuntu's releases just signify the date it was released: 10 is the year (2010), 4 is the month (April).
10.4 is still in beta though. Beta can have bugs that are solved if a current release is used. (10.04)

---

### Post by WorMzy on 2010-08-06
10.04 is the current release and has been out since April, it's not a beta. :S

I think you're thinking of 10.10.

---

### Post by xykivo on 2010-08-06
It's definitely possible.

You can use python (preferably python 3) java script module to connect with google APIs.

You can then use google APIs search to look for videos and download the html result somewhere.

If you are looking for a way to download videos with a script, u can use python to parse the result of the search, and then activate a torrent client to download.

---

