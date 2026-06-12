---
title: "WGET downloading ASP links with query strings"
date: 2010-09-24
forum: General Help
---

### Post by mihnea.radulescu on 2010-09-24
Hello everybody!

I'm trying to download a website that contains mostly just a few dynamic asp pages, linked among themselves with various query strings.

Example:
home.asp has links only to itself with lots of query string variations, links that retrieve completely different data from the DB

I would like to know how to set up wget to see each "home.asp" link (with particular query string) as a different web page and download it as such.

All the very best,
Mihnea

---

### Post by dcstar on 2010-09-25
> **mihnea.radulescu said:**
> Hello everybody!

I'm trying to download a website that contains mostly just a few dynamic asp pages, linked among themselves with various query strings.

Example:
home.asp has links only to itself with lots of query string variations, links that retrieve completely different data from the DB

I would like to know how to set up wget to see each "home.asp" link (with particular query string) as a different web page and download it as such.


Do you understand what a Dynamic Website is?

---

### Post by mihnea.radulescu on 2010-09-27
The most dynamic web page is to the user's browser as ordinary an HTML page as any static web page. Might set up some cookies to the user, but that's about it. The difference is only on the server side.

My question was very simple, considering that home.asp has links to home.asp?x=y and home.asp?a=b&c=d, requests which retrieve completely different HTML files (at least on the site in question), how can I set WGET to consider each link+query string as a separate entity and request them as such, instead of just downloading home.asp and then stopping, seeing that all the links point, in fact, to the same file. The links I need are, of course, present in the home.asp file.

Regards,
Mihnea

---

### Post by refractal on 2011-01-16
this sort of thing works for dealing with asp in a redirection:

wget --output-document=traffic_$(date +\%Y\%m\%d\%H).gif "http://sm3.sitemeter.com/rpc/v6/server.asp?a=GetChart&n=9&p1=sm3lifehacker&p2=&p3=3&p4=0&p5=64\%2E249\%2E116\%2E138&p6=HTML&p7=1&p8=\%2E\%3Fa\%3Dstatistics&p9=&rnd=7209"

---

