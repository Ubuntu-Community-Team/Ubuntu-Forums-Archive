---
title: "How to Print To PDF by default? (Windows makes this a lot easier)"
date: 2011-05-08
forum: General Help
---

### Post by ester4 on 2011-05-08
I'm having three problems.

1.) when I hit ctrl + P the print screen comes up but the focus is on the "General" tab. HOw do I get the focus to automatically be on "Print to File"?

2.) if I use the mouse to select "Print to File" the radio button for PS is selected. How do I get the radio button for PDF to automatically be selected?

3.) How do I get the name of what I am printing to auto-populate into the PDF's Name-field? 

I came back to Ubuntu to try Unity and like Unity a lot. But this PDF problem is a big one. With Windows I can use PDF Creator and I hit ctrl + P and tap Enter and a PDF is automatically saved to the folder of my choice with the name auto-populated to the Saved File-Name. It's stuff like this that makes using Windows a lot easier than Ubuntu. Any way I can get this ease of use in Ubuntu for creating PDFs from Firefox?

I'd really appreciate some help. thanks

PS: I don't have a printer installed. I'm on the road a lot and need to "print" things to PDF for later use in Work settings.

---

### Post by edm1 on 2011-05-08
I agree that it should be possible to set print to pdf as a default. You may be able to [achieve this using cups-pdf]("http://www.ubuntugeek.com/how-to-create-pdf-documents-in-ubuntu.html"), although that article is quite old now.

---

### Post by ester4 on 2011-05-08
> **edm1 said:**
> I agree that it should be possible to set print to pdf as a default. You may be able to [achieve this using cups-pdf]("http://www.ubuntugeek.com/how-to-create-pdf-documents-in-ubuntu.html"), although that article is quite old now.

I checked Ubuntu Software Center and Synaptics. There is no listing for "cups-PDF"

Anyone know why not?

---

### Post by dragonfly41 on 2011-05-08
I've just checked and I believe that the names in Synaptic Package Manager (and I guess elsewhere) are simply case sensitive

so cups-pdf is found
but cups-PDF is not found!


I'm having my own problems in printing *.pdf  .. I've installed Okular.

---

### Post by nrundy on 2011-05-08
I used to use PDFCreator in Windows too. Here guys:

[http://www.liberiangeek.net/2010/09/add-pdf-printer-ubuntu-10-0410-10-maverick-meerkat-cups-pdf/](http://www.liberiangeek.net/2010/09/add-pdf-printer-ubuntu-10-0410-10-maverick-meerkat-cups-pdf/)

follow the directions in above link to install "cups-pdf" in Ubuntu Software Center. ester: cups-pdf won't install if you are running the LIVE CD. If you are, this is why it won't come up in USC. 

Once installed, make the cups-pdf printer your DEFAULT printer. then ctrl + P, Enter will do exactly what PDFCreator did in Windows, including adding the Name to the saved file.

---

### Post by edm1 on 2011-05-08
> **ester4 said:**
> There is no listing for "cups-PDF"

You will find that most things in linux are case sensitive.

---

