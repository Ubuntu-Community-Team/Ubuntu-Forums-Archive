---
title: "Help me please!"
date: 2011-02-22
forum: General Help
---

### Post by marclane on 2011-02-22
Hi,

Ok, this problem is so serious I feel like hitting something. I'm in  Ubuntu 10.10, and wrote an Essay in OpenOffice. I saved and everything  last night, I'm positive of this. This morning, however, when I went to  go print it, the document was GONE. Not only, but in Recent Documents,  it sees my document, it just says not found. It's not in my trash. I've tried searching for it, but nothing.

It's as if it didn't save at all, but it did, or it wouldn't even appear in the file>recent documents, and it does. Just won't let me open it.

Please help, my essay is due in less than two hours

oh and I saved as a doc (the 97/xp one) if that helps

---

### Post by ~LoKe on 2011-02-22
See if you can find it.

```
updatedb && locate (filename).doc
```

---

### Post by marclane on 2011-02-22
Nothing... I'm becoming desperate! It's a 12 page paper, I can't possibly rewrite it!

---

### Post by ~LoKe on 2011-02-22
> **marclane said:**
> Nothing... I'm becoming desperate! It's a 12 page paper, I can't possibly rewrite it!

Did you replace (filename) with the actual filename?

---

### Post by kc1di on 2011-02-22
go to Places > find file> search for the file by name  make sure to search the whole system.  

you can also do a search for all .doc files by entering *.doc

Good Luck

---

### Post by marclane on 2011-02-22
Yes, I did replace filename with the actual filename. It gave me no results.

I tried doing a search of the file system with no avail, i'll try searching all my docs see what happens.

---

### Post by ~LoKe on 2011-02-22
> **marclane said:**
> Yes, I did replace filename with the actual filename. It gave me no results.

I tried doing a search of the file system with no avail, i'll try searching all my docs see what happens.

If locate didn't find it, I'm sorry, but it's gone.

---

### Post by Kilroy2011 on 2011-02-22
When it's from today, saved after midnight:

cd to /

```
find . -daystart -mtime 0 | grep doc$
```from yesterday:

```
find . -daystart -mtime 1 | grep doc$
```When it ended in the /tmp and you rebooted, it may be gone - sorry

---

### Post by marclane on 2011-02-22
But why?! Why would my computer do this to me the day of my assignment? Can I prevent this from happening again?

---

### Post by ~LoKe on 2011-02-22
> **marclane said:**
> But why?! Why would my computer do this to me the day of my assignment? Can I prevent this from happening again?

Save it more carefully next time, and verify that the document actually exists after you've saved it before closing.

---

### Post by grahammechanical on 2011-02-22
I use Open Office. If I switch off the computer without closing Open Office then the next time I load the program I am asked to restore the documents. Open Office automatically saves documents. So, you only lose the work that you put in the documents since the last auto save action. Have you switched this feature off? Where does Open Office normally save your documents? Did you use the Open file dialog with All Files as the file type? Or did the select they file type that you choose to save the file as?

Regards.

Try going to Places>Home Folder. Clicking Show Hidden files and look for a folder called .openoffice.org (note the dot in front of the name). Open that folder then open the folder called 3 (for openoffice 3 or 2 if you are using openoffice 2), then the folder called user. Then the folder called backup. That is where the documents that I have been working on today are saved proir to closing the program.

---

### Post by gandaran on 2011-02-22
did you rename the .doc file when saving or was it just .doc? doesn't open-office saves files in home directory by default or did you specify a location for saving?
look in the home hidden files, if it was just .doc it will be there at the bottom page.

---

### Post by Vaphell on 2011-02-22
general advice: never depend on a single copy of the file you can't afford to lose. This is certainly a painful lesson to lose work just before the deadline, but a valuable one nonetheless and you will reap profits of it in the future.

Corruption/data loss can happen for whatever reason (power loss, hdd failure, software glitch, forced termination, careless delete/format in the wrong place) and you are hosed. Save quite frequently and with different names to have access to older versions and drop them from time to time to some other place - online storage, pendrive, dvd, whatever. Also look in open office preferences for automatic backup options and make sure they are enabled.

---

### Post by coldraven on 2011-02-22
OO should have been auto-saving every 15 minutes .
You can set  OO to always have a backup of the current document. 
See screenshot

---

### Post by blackcobra on 2011-05-28
have a look a dropbox, if you save your docs in the dropbox folder, it saves your documents automatically to the web! Then, you can access them on any computer that has the web! and it also saves your docs on all the computer in which dropbox is installed! meaning that your docs will be store on all your computers with dropbox!

[http://www.techdrivein.com/2010/09/how-to-install-dropbox-in-ubuntu-lucid.html](http://www.techdrivein.com/2010/09/how-to-install-dropbox-in-ubuntu-lucid.html)

It comes with 2gbs free! basically, its like a 2gb memory backup!

---

### Post by Thewhistlingwind on 2011-05-28
Personally, I send documents from my laptop to my desktop and use it as a fileserver. 

That way I can take advantage of the better ergonomic resources on my desktop, and backup in the process. (Without having to trust the cloud not to read my data.) 

You may want to try testdisk to recover your files. 

sudo apt-get install testdisk

This may do damage to your filesystem though, use at own risk.

---

### Post by lmn. on 2011-05-28
DROPBOX
..that really sucks :(

---

### Post by linuxinstalledfromhdd on 2011-05-28
You can also use the one that comes with Ubuntu, namely Ubuntu One.  There has to be several different free cloud sync storage applications you can use with Ubuntu these days.  Always burn yourselves a rescue disc for later just in case too. Just a tip.:P

---

