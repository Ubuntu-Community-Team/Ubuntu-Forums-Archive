---
title: "Opening pdf files from Mozilla Firefox does not work"
date: 2009-10-01
forum: General Help
---

### Post by sh-tfish on 2009-10-01
When  I click link to pdf file in Firefox I get pop up where I can choose either to download it or open it. Open is linked with evince, but it does not work. I am getting error message that evince is not installed. It is not true - I can open files with ease if I download them. Could this problem be caused by missing pdf association in Firefox? Please help, I am tired of downloading files.

See screenshots from process in atachments (in czech language).[URL="http://img34.imageshack.us/img34/6749/pdf3.png"]
[/URL]

---

### Post by lovinglinux on 2009-10-01
Try [PDF Download](https://addons.mozilla.org/en-US/firefox/addon/636) extension. It works for me.

---

### Post by Guy Sibley on 2009-10-01
I like Foxit Reader, or just open the pdf with document viewer

---

### Post by sh-tfish on 2009-10-02
> **lovinglinux said:**
> Try [PDF Download]("https://addons.mozilla.org/en-US/firefox/addon/636") extension. It works for me.
Yes. It works fine. But I didn't want to use extension for thing that should work without it. I am trying to keep number of extensions in Firefox as low as possible.

> **Guy Sibley said:**
> I like Foxit Reader, or just open the pdf with document viewer
I think, you did not understand me. I can open pdf document if I choose to download it and then open it by clicking on it. But if I choose to open it right from pop-up, I get error message. 

BTW: "Document viewer" is Evince ;)

---

### Post by benmoreassynt on 2011-03-17
Try locating and deleting the file mimetypes.rdf, and then restarting Firefox. Worked for me.

mimetypes.rdf will be in the session settings directory. Something like:

/home/username/.mozilla/firefox/nvdjfsghsd.default/mimetypes.rdf

---

