---
title: "PDF no text - urgent please (I'm in Japan)"
date: 2011-03-14
forum: General Help
---

### Post by jonlink on 2011-03-14
I am in Japan right now and I need to read a pdf to find out more information about the areas of rolling blackouts. The pdf from tepco has no text though! This has happened with ubuntu before. How can I fix it?

I am using document viewer.

---

### Post by rubylaser on 2011-03-14
How about a link to the document so that others can see what you're trying to open? Nevermind, I think I found them below.

---

### Post by rubylaser on 2011-03-14
This is what they posted on the 14th... Below Should be the pdfs.  I hope you're safe.
```
Due to the Tohoku-Chihou-Taiheiyo-Oki Earthquake occurred on March 11, 
the power supply-demand balance within our service area has been very 
critical. As such, we have decided to implement rolling blackout on 
and after March 15, which was started on March 14. We sincerely regret 
to cause the anxiety and inconvenience to our customers and the society.
We will continuously make every effort to restore stable power supply 
as soon as possible. 

&#9675;Implementation plan of rolling blackout on Tue, March 15
  Regional block and time periods planned to have rolling blackout are as 
  follows. The actual extension of blackout for each block are planned to 
  be approximately 3 hours each. 
  For customers who will be subject to rolling blackout, please be prepared 
  for the announced blackout periods. Also for customers who are not 
  subject to blackouts, TEPCO appreciates your continuous cooperation in 
  reducing electricity usage by avoiding using unnecessary lighting and 
  electrical equipment. 

[Expected rolling blackout regions]
Block 3: 6:20 - 10:00 
Block 4: 9:20 - 13:00 
Block 5: 12:20 - 16:00 
Block 1: 15:20 - 19:00 
Block 2: 18:20 - 22:00 

&#9679;Please refer to the attachment1 for the detailed region of the blocks.
&#9679;Starting and ending time of blackout periods may slightly differ. 
&#9679;Depending on supply and demand conditions on the actual days, 
  planned blackouts may not been carried out or may be implemented at 
  times which were not previously announced. 
&#9679;The website of TEPCO provides information including "Chome". 
  http://www.tepco.co.jp/index-j.html

&#9675;Implementation plan of rolling blackout from Wed, March 16 to Fri, March 18
  Please refer to the attachment2 for the detailed plan. 

&#9679;Please refer to the attachment1 for the detailed region of the blocks. 
&#9679;The rolling blackout is scheduled in the same order every day, but 
  time of blackout periods may be subject to change. 
&#9679;Starting and ending time of blackout periods may slightly differ. 
&#9679;Depending on supply and demand conditions on the actual days, 
  planned blackouts may not been carried out or may be implemented at times which 
  were not previously announced.
```
Here are all of the their pdf's with updates, I've downloaded and saved from Google Docs for you.  These work fine for me now.

---

### Post by jonlink on 2011-03-14
Thanks, but the files don't say which number the groups are, I can see my city in the first file on the list. Is that group 1?

---

### Post by rubylaser on 2011-03-14
I thought the group number was right at the top of each pdf under the date and time, so the March 15,2011	15:20~19:00 is the one that says Group 1 (the 4th pdf). That should be your Group I believe.

---

### Post by grahammechanical on 2011-03-14
I am able to open these PDFs in document viewer. I have just checked. The fonts being used are truetype and they are not embedded. (see File>Properties). I guess that if you do not have the chosen truetype font on your system, then all you see is a blank page. I have a set of MS truetype fonts installed on my system. Perhaps that is why I can see the text. 

When I create a PDF document I choose to have the font embedded. Then they can be read by people who do not have the open source fonts that I am using on their system.

Search synaptic for ttf-mscorefonts-installer.

Regards.

---

### Post by duuchung on 2011-04-30
Dear pals,
I need help from a guru in pdf and ubuntu.
I upgraded to a new version with utf-8 of webERP, an accounting system.
In webERP, tcpdf is used to work around pdf to generate Asian and Arab characters in utf-8 format. I got a blank PO with only my company logo and black lines printed.

The error message. 

Error message: 
Notice: Undefined offset: 0 in /var/www/webERP/includes/class.pdf.php on line 303
…………..
…………..
Warning: Cannot modify header information - headers already sent by (output started at /var/www/webERP/includes/class.pdf.php:303) in /var/www/webERP/includes/tcpdf/tcpdf.php on line 5817 
TCPDF ERROR: Some data has already been output to browser, can't send PDF file

I checked class.pdf.php on line 303, there reads: “$ l+=$cw[$i];” 

I am an open source supporter working with ubuntu 10.04. 
I downloaded the newest version of tcpdf v5_9_074 from sourcegorge. 
I replaced the whole tcpdf directory. 
I copied javiergb.php, which contains the Chinese characters for webERP and TCPDF purposes, to tcpdf. 
I still got a blank PO with my company logo and black lines. 
I sent it to a window XP machine. 
I opened the PO. 
I saw the beautiful and bold English words and Chinese characters. 
I sent the PO in window XP back to ubuntu.
It could not opened in ubuntu.
What's the problem remaining? 
A PDF document can be read in window xp but not ubuntu.
A tcpdf issue? A pdf issue? A ubuntu issue?
Best regards,
dxxc

---

### Post by duuchung on 2011-04-30
This is a ubuntu problem.

---

### Post by 5149.5 on 2011-04-30
You could try the PDFescape extension for Firefox. With it, you can open the pdf in FF without the use of another program.

---

