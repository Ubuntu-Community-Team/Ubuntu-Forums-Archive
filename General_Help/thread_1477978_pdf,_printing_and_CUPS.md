---
title: "pdf, printing and CUPS"
date: 2010-05-09
forum: General Help
---

### Post by kmarzi on 2010-05-09
Hello,

Newby to Ubuntu here. I've just installed CUPs in order to print pdf  docs. Unfortunately, it doesn't seem to work. In fact, I can't seem to  print anything now (the print to file function isn't working now  either). When I try to print with the pdf printer which now appears after installing CUPs, I basically receive this message:

[I]Print Error.

There was a problem printing document ´document name here': 'Stopping job because the scheduler could not execute the backend.''[/I]

So, I guess my questions are as follows:

1) I was wondering if anyone knows what I'm doing wrong i.e. why I can't print to pdf?

2) If not, maybe I should just uninstall CUPs? Any idea how I  can do this? I've looked for it in Ubuntu Tweak but I can't seem to find  anything. I've also searched in the Ubuntu Forums for advice but,  again, I can't find anything.

Hope you can help.
kmarzi

---

### Post by meho_r on 2010-05-09
Did you restart cups after installing cups-pdf?
```

sudo /etc/init.d/cups restart

```
(or restart your computer) :)

If you still have problems, try [this.](http://www.ubuntugeek.com/how-to-create-pdf-documents-in-ubuntu.html)

---

### Post by kmarzi on 2010-05-09
Hey, thanks for that. I have tried to follow the instructions (on the  website which you've posted) previously. I still had no joy. I've  uninstalled CUPS and I still can't seem to pdf certain things. However, I can now pdf from the web (e.g. Mozilla) just by using the standard "print to file function". I think I might just stick with that. 

Do you think that it's actually necessary to install CUPS? I usually just pdf things from the internet (which seems to be working now) and use the pdf function within open office for documents.

Thanks again.
Kmarzi

---

### Post by meho_r on 2010-05-09
For printing in pdf, you actually need cups-pdf, which installs a virtual printer serving for creating pdf file (files are written to ~/PDF folder). CUPS is a printing system needed for printing in general.

---

### Post by kmarzi on 2010-05-10
That still doesn't work. I've followed the instructions on the link you provided. I still get the same error message. I've also restarted CUPs via the terminal as you suggested. Still no joy. 

I am unable to totally follow the instructions on the website you provided (I'm not sure whether that's because I'm using 10.04 and the instructions might have been for an earlier version?). But, for example, when I go into the printer properties, and try to change the "make and model" as instructed, I am unable to select "Postscript Color Printer" (the option isn't available) and instead I am forced to select Generic CUPS-PDF Printer.

I'm also not sure whether this command is working: sudo chmod +s /usr/lib/cups/backend/cups-pdf. This doesn't seem to do much in the terminal when I paste it. Indeed, the problem seems to be something to do with the "backend"... Whatever that might be.

Thanks for all your help with this. As an Ubuntu newbie, simple installations are proving to be very tricky indeed...

kmarzi

---

### Post by captainron042 on 2010-05-13
^ ditto

---

### Post by luddek on 2010-06-13
I got the same error message and then i used these three commands:
```
sudo chmod 700 /usr/lib/cups/backend
sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo /etc/init.d/cups restart
```
And then it worked

---

### Post by dmp2010 on 2010-10-08
My pdf printer is working but it only prints first page. Any help will be appreciated.

---

### Post by jbejar on 2010-12-04
I was able to get this to work by
creating the directory ~/PDF, and reinstalling the packages.


mkdir ~/PDF
sudo apt-get remove cups-pdf
sudo apt-get install cups-pdf

And the printer was already working (I did not have to do anything else

---

