---
title: "Firefox 'Print to File'  - how to get the filename fo default to web page title?"
date: 2012-02-29
forum: General Help
---

### Post by chamira on 2012-02-29
Hello,

I would like to know if there is a way of making Firefox's 'Save to File' option to bring up the web page tile as the default 'Name' (i.e filename). 

At the moment it just offers 'Mozilla.pdf', so I would have to type or copy and paste a title every time.

Also, is there a way for the making the browser session remember the folder location of where I saved a file last time. At the moment it simply defaults to my home drive.

I have looked in Firefox's 'about:config' but I can't find anything.

---

### Post by lovinglinux on 2012-02-29
If you are trying to save a file link, it will use the original file name. If you are trying to save a page, it will use the page name.

About the session, as far as I know, it will remember the last used folder only. You could use an extension like [Automatic Save Folder](https://addons.mozilla.org/en-US/firefox/addon/automatic-save-folder/?src=search) to filter specific domains and file types and save automatically on different folders.

---

### Post by chamira on 2012-03-03
> **lovinglinux said:**
> If you are trying to save a file link, it will use the original file name. If you are trying to save a page, it will use the page name.

I agree with you here!  But I am talking about saving a page as a PDF/Postscript file via File > Print > Print to File.

The name simple defaults to 'mozilla.pdf'

---

### Post by efflandt on 2012-03-03
Install cups-pdf.  It is under **More Info** for **Cups** in Software Center, or you could [B]sudo apt-get install cups-pdf
[/B]
If you print to that it saves it in ~/PDF under the name of the page like Receipt_PrinterFriendly_asp_OrderID_52900.pdf

It would be good practice to rename certain dynamic pages you want to save.  For example if you save something like Airline Reservation Confirmation, it would overwrite a previous Airline_Reservation_Confirmation.pdf

---

### Post by chamira on 2012-03-03
> **efflandt said:**
> Install cups-pdf. 

Thank you, this looks what I have been after.

Now I just need to find how to tweak the configs....[http://www.cups-pdf.de/documentation.shtml](http://www.cups-pdf.de/documentation.shtml)

---

