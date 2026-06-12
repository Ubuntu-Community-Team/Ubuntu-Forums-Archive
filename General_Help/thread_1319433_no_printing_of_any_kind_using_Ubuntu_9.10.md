---
title: "no printing of any kind using Ubuntu 9.10"
date: 2009-11-08
forum: General Help
---

### Post by chasmwis on 2009-11-08
it is now three weeks and two legal pads of notes taken from every forum and chat page I can find on the Operating system. i'm not new to the Ubuntu family but i find the support system problematical. As with the early system I never got the answers I needed to what I thought were simply requests. i love the new 9.10 release, but to drop windows for good I need a printer that actually works. I own three printers, Canon, Lexmark x1270 and a compaq.
After following all instructions I can find none of them print.
Question: How do I get a simple Canon Pixma iP1500 to print with Ubuntu 9.10.
please, be as detailed as possible, this has become very fustrating

Thank you
Chuck

---

### Post by Druke on 2009-11-08
list all your model numbers please.
[SIZE="1"]Also note: unless you are paying for commercial canonical support, everyone here is just a regular Joe that likes helping in free time. Sorry that you are having trouble.[/SIZE]

---

### Post by P4man on 2009-11-08
Hi,

You have to understand support here is a community effort. All volounteers (users, just like you) giving help where they can and when they can, but often there is simply too much demand for help and not enough people to help.

If you're not happy with that, there is an alternative route and that is commercial support. For a very modest fee you can get professional support from Canonical here:
[http://shop.canonical.com/product_info.php?currency=USD&products_id=528](http://shop.canonical.com/product_info.php?currency=USD&products_id=528)

A quick google on your printer and adding ubuntu throws up a lot of results but admittedly not very easy ones, and they dont seem to work for everyone. One possible solution however is this:
[http://www.turboprint.info/](http://www.turboprint.info/)

Again its not free though.

Ill try a bit harder to find a good solution that appears to work reliably and then talk you through it, but no guarantees.

---

### Post by chasmwis on 2009-11-08
Thank you for your quick response.
the two printers I would like to use are 
Canon Pixma iP1500
Lexmark x1270 three in one. printer copier and fax.
The canon unit is what I currently have connected to my tower.

Chuck

---

### Post by Druke on 2009-11-08
for the pixma [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500)

---

### Post by P4man on 2009-11-08
> **Druke said:**
> for the pixma [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500)

Good find. Though these instructions are for older versions of ubuntu they do seem to work with one small change:

remove libxml1 from this command:

```
sudo apt-get install alien **libxml1**
```

so instead just run

```
sudo apt-get install alien
```

That allows me to install the packages but without printer I obviously cant tell if it works.

---

### Post by Druke on 2009-11-08
Lexmark is Notoriously bad with [s]ubuntu[/s] Linux.

you cant try your luck [here]("http://www.google.com/search?hl=en&q=+site:ubuntuforums.org+ubuntu+Lexmark+x1270&ei=kRf3SpmeCMPP8QaJ3tTzCQ&sa=X&oi=forum_cluster&resnum=1&ct=more-results&ved=0CA0QrQIwAA")

---

### Post by P4man on 2009-11-08
Nod. Vote with your wallet next time and avoid lexmark at all cost. That also includes Dell printers which are just rebranded lexmarks.

HP is top when it comes to supporting linux, you should have no problem with almost any HP printer, drivers will be included in ubuntu by default.  Epson is pretty good too, they support most of their stuff through drivers from [avasys]("http://avasys.jp/eng/linux_driver/download/")

As for the compaq, can you give us the type?

---

### Post by chasmwis on 2009-11-08
Thank you all............
I'm off to try again.........
Try, Try , again if at first you don't succeed...........
I'll keep in touch as to any progress or the lack of it..........
This encounter has restored my faith in Linux users and I thank you.

Chuck.

---

### Post by chasmwis on 2009-11-08
Greetings to all............
As I have great news.............the Canon.................PRINTS!!!!!!!!!!!!!!!!!!!
I have stumbled on one thing, I'm not sure what program is running what???????
Over the last three weeks I have downloaded multitude of programs. One of the was turboPrint trial version.
Well who cares, if things keep printing after 30 days I'm home free...........If not....
back to the drawing board.
But for now it.............PRINTS

Thanks again to all
PS I'll keep in touch

Chuck:D):P

---

### Post by Druke on 2009-11-08
if you run into problems just reply again, we'll all get emails.

---

