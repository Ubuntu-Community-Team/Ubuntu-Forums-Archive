---
title: "Viewing PDFs in web browser. Is it possible?"
date: 2011-10-10
forum: General Help
---

### Post by algar32 on 2011-10-10
I need to view this pdf in my web browser because i can not download it. Firefox looked for the necessary plugin to view pdfs in the web browser and found nothing. I really need help here. Is it possible? Is xubuntu capable of such a daunting task?

---

### Post by ibutho on 2011-10-10
You need to install Adobe Reader. You can download the deb file from Adobe website or install from the partner repo using apt-get.

---

### Post by jwbrase on 2011-10-10
> **algar32 said:**
> I need to view this pdf in my web browser because i can not download it.

Why not?

---

### Post by lovinglinux on 2011-10-10
Personally, I do not recommend Adobe reader. Is a huge 290 Mb application and they won't support Linux anymore. I don't know which PDF viewer comes with xubuntu, but you should be able to use the default one in conjuction with mozplugger plugin. You can install it from the Software Center or via terminal:

```
sudo apt-get install mozplugger
```

Another alternative would be to use an add-on that enables reading the PDF files through Google Docs. I use [gPDF](https://addons.mozilla.org/en-US/firefox/addon/14814/)

---

### Post by algar32 on 2011-10-10
It was unable to locate any of my packages in terminal when i did the sudo get app thing.  How do I unlock the pacakges.

---

### Post by lovinglinux on 2011-10-10
> **algar32 said:**
> It was unable to locate any of my packages in terminal when i did the sudo get app thing.  How do I unlock the pacakges.

I don't understand what you mean. What happened when you entered the command and your password?  If you are experiencing difficulties with the command-line, use the Software Center.

---

### Post by algar32 on 2011-10-10
I ended up using the software center but it did not install the firefox addon. thats why i was trying the command line.

---

### Post by algar32 on 2011-10-10
How do I get the firefox addon?

---

### Post by dniMretsaM on 2011-10-10
I would recommend installing this Firefox add-on: [Google Docs Viewer](https://addons.mozilla.org/en-US/firefox/addon/google-docs-viewer-pdf-doc-doc/?src=search). This will open up the PDF in the Google Docs viewer. Not sure if you need a Google account or not.

---

### Post by algar32 on 2011-10-10
We did it!!!! I got it to work with yoour help!!! You all rule!!!!!

---

