---
title: "Link to upload folders to Google Docs"
date: 2012-02-23
forum: General Help
---

### Post by AmpersUK on 2012-02-23
Is there an easy way to upload folders from my Ubuntu 11.10 Unity Desktop straight to Google Docs?

An easy way, I am happy using Terminal but get very confused with tar or zip folders and scripts?

---

### Post by LewisTM on 2012-02-23
Here's what worked for me:
Followed the instructions from [here]("http://doctormo.org/2010/07/20/google-doc-mount/comment-page-1/#comments").
1) Run
```
sudo apt-add-repository ppa:doctormo/ppa

```
2) In your Software Sources editor, find the doctormo entries and edit them. Change oneiric for lucid in the Distribution field.

3) Back in the terminal, run
```
sudo apt-get update && sudo apt-get install gdocs-mount-gtk -y
```
This will install the front end and backend softwares for accessing Google Docs

4) Method #1: Launch Google Docs Connection. Enter your info and press OK. Nautilus will open up with your Google documents mounted in a temporary dir.

3) Method #2: Create a directory wherever you want.
Run 
```
gmount email password directory
```
This will mount your Google docs in there. To unmount:
```
gumount directory
```
Reference: [http://code.google.com/p/google-docs-fs/wiki/OnlineManual](http://code.google.com/p/google-docs-fs/wiki/OnlineManual)

Cheers!

---

### Post by AmpersUK on 2012-02-24
> **LewisTM said:**
> Here's what worked for me:

4) Method #1: Launch Google Docs Connection. Enter your info and press OK. Nautilus will open up with your Google documents mounted in a temporary dir.

3) Method #2: Create a directory wherever you want.
Run 
```
gmount email password directory
```This will mount your Google docs in there. To unmount:
```
gumount directory
```Reference: [http://code.google.com/p/google-docs-fs/wiki/OnlineManual](http://code.google.com/p/google-docs-fs/wiki/OnlineManual)

Cheers!

Hi, I have managed to do everything up to the bits within the above quote, but here I have become stuck.

Could you please rewrite these but pretend? you are writing them for an idiot! Then I might be able to get this working :-)

Ampers

---

### Post by LewisTM on 2012-02-24
All right. We never know the level of knowledge of forum members and flooding posts with details is frowned upon, unless it's necessary.

So the software is installed. You should have a new menu item in Accessories/Google Docs Connection, that the dash should find for you. That's what you want to try first. The command [FONT="Courier New"]gdocs-mount-gtk[/FONT] will also launch it.

If you want to automate the process for instance with a startup job, you can use the command line interface and the gmount command. This requires that you create a directory, for example "GoogleDocs" in your home folder. Then you just enter the gmount command followed by your email address (=Google Docs username), your password and the name of the directory (/home/user/GoogleDocs). This directory will become your GoogleDocs folder and you can add, edit or delete files. You will be limited to OpenDocument formats.

That's it! Storing your Google Docs password in a startup job may  be handy but insecure; what we have here is a primitive piece of software. You can remedy that by encrypting your home directory or by entering your password every time with the GTK tool.

---

