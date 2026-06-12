---
title: "Software for a scanning kiosk"
date: 2011-06-21
forum: General Help
---

### Post by Agg23 on 2011-06-21
For a client I need to make a scanning kiosk.  It is to operate by pressing the scan button on the scanner, then saving that scanned file onto a server.

Is there a way to use SANE to do that?

Thank you very much,
agg23

---

### Post by Agg23 on 2011-06-22
Anyone?

---

### Post by Derxst on 2011-06-22
Your solution might be a standalone scanner that can scan directly to a file share. What is your budget?

---

### Post by pqwoerituytrueiwoq on 2011-06-22
i am nost usre what kiosk means as best i can figured from a quick google search is it is a rapid scan is it like scanning multiple pages with a document feeder?
by any change may I see the scanners help info
[FONT=Courier New]scanimage --help[/FONT]
document feeder is a feature i would like to add so a [thing]("http://ubuntuforums.org/showthread.php?t=1519201&page=12#116") i have been working on just need a way to integrate it in to the ui

---

### Post by Agg23 on 2011-06-22
> **Derxst said:**
> Your solution might be a standalone scanner that can scan directly to a file share. What is your budget?

My client's budget is no more than $200.  He also prefers to use a HP product (don't ask me why).  The only network aware scanner that HP offers is almost $900.  So I want to recreate that by using a small computer to do the network handling for the scanner.

> **pqwoerituytrueiwoq said:**
> i am nost usre what kiosk means as best i can figured from a quick google search is it is a rapid scan is it like scanning multiple pages with a document feeder?
by any change may I see the scanners help info
[FONT=Courier New]scanimage --help[/FONT]
document feeder is a feature i would like to add so a [thing]("http://ubuntuforums.org/showthread.php?t=1519201&page=12#116") i have been working on just need a way to integrate it in to the ui

No.  By a kiosk I mean you walk up to this desk with a scanner on it, hit the scan button, and your document is scanned and put a network share.  A document feeder is not necessary.

**Edit:**  What you made is interesting pqwoerituytrueiwoq, but I don't need the scanner to be accessed anywhere else.  I just need the scanned files to be accessible.

---

### Post by Derxst on 2011-06-22
> **Agg23 said:**
> My client's budget is no more than $200.  He also prefers to use a HP product (don't ask me why).  The only network aware scanner that HP offers is almost $900.  So I want to recreate that by using a small computer to do the network handling for the scanner.



No.  By a kiosk I mean you walk up to this desk with a scanner on it, hit the scan button, and your document is scanned and put a network share.  A document feeder is not necessary.

**Edit:**  What you made is interesting pqwoerituytrueiwoq, but I don't need the scanner to be accessed anywhere else.  I just need the scanned files to be accessible.

I have a HP All-in-one scanner with a scan button. It scans and I am prompted to save it at a location. That location could easily be a file share.

If your client wants "push a button and the scan shows up in file share" with no additional work, that is going to require a scanner that is more expensive and out of his/her price range.

---

### Post by pqwoerituytrueiwoq on 2011-06-22
> **Agg23 said:**
> My client's budget is no more than $200.  He also prefers to use a HP product (don't ask me why).  The only network aware scanner that HP offers is almost $900.  So I want to recreate that by using a small computer to do the network handling for the scanner.



No.  By a kiosk I mean you walk up to this desk with a scanner on it, hit the scan button, and your document is scanned and put a network share.  A document feeder is not necessary.

**Edit:**  What you made is interesting pqwoerituytrueiwoq, but I don't need the scanner to be accessed anywhere else.  I just need the scanned files to be accessible.
if you can get the scan button to save a file on the server it will be really easy
i would try to figure out how but my new all in one does not have a scan button (old one craped out after being fixed like a dozen times) wait a munite i have a second scanner hooked up but the buttons don't do anything
edit if your objective is to get scans onto the network you could use the scanner server to scan and all images will be on the network

---

### Post by Agg23 on 2011-06-22
> **pqwoerituytrueiwoq said:**
> if you can get the scan button to save a file on the server it will be really easy

if your objective is to get scans onto the network you could use the scanner server to scan and all images will be on the network

I'm not sure what you mean by these.  The first thing is exactly what I want to do.

The second is also what I want but I am not sure what you mean by the scanner server.

Thanks for all of your help,
agg23

---

### Post by pqwoerituytrueiwoq on 2011-06-22
> **Agg23 said:**
> I'm not sure what you mean by these.  The first thing is exactly what I want to do.

The second is also what I want but I am not sure what you mean by the scanner server.

Thanks for all of your help,
agg23
[http://ubuntuforums.org/showpost.php?p=10796554&postcount=116](http://ubuntuforums.org/showpost.php?p=10796554&postcount=116)
that
when it makes a scan it is stored on the server and is accessible by anyone with access to the server 
it will do what you want and more
if you need/would like a demo send me a pm

---

### Post by Agg23 on 2011-06-22
> **pqwoerituytrueiwoq said:**
> [http://ubuntuforums.org/showpost.php?p=10796554&postcount=116](http://ubuntuforums.org/showpost.php?p=10796554&postcount=116)
that
when it makes a scan it is stored on the server and is accessible by anyone with access to the server 
it will do what you want and more
if you need/would like a demo send me a pm

So basically you hit the scan button then you can access the image from http?

That would be perfect.

---

### Post by pqwoerituytrueiwoq on 2011-06-22
just the button is on the web page but everyone can view the scan and you can scan it from any computer in the network
 i think i just got the next version ready
if you would like to view http interface send me a message it will be slow cause my upload speed is garbage (160 Kbps)

---

### Post by Agg23 on 2011-06-22
What do you think the system requirements for this are?  Just anything that will run Apache and PHP?

---

### Post by SoFl W on 2011-06-22
I know you said your client prefers HP.  I have an Epson Workforce 610 all-in-one, that can scan on the unit to a PDF or JPG, and store the files on unit's memory card. (not included)  This memory card is accessible as a network share.  It cost me $99, but I think that price was a mistake when I purchased it, I usually see it for $199.99 (USD)

---

### Post by Agg23 on 2011-06-22
> **SoFl W said:**
> I know you said your client prefers HP.  I have an Epson Workforce 610 all-in-one, that can scan on the unit to a PDF or JPG, and store the files on unit's memory card. (not included)  This memory card is accessible as a network share.  It cost me $99, but I think that price was a mistake when I purchased it, I usually see it for $199.99 (USD)

He said he prefers HP yes, but when I asked him why he said because of their software.  Since (obviously) we won't be using HP's software with this, I wonder if I can convince him otherwise.

I was looking and found [this]("http://www.microcenter.com/single_product_results.phtml?product_id=0343063").  It is fairly cheap and meets all of his specifications except for it being HP.  It is also fully compatible with SANE (which is the biggest reason for buying it).

---

