---
title: "evolution ate two of my address books"
date: 2009-08-31
forum: General Help
---

### Post by morganpatrick on 2009-08-31
So I copied my .evolution folder from one computer to another and when I opened the my migrated evolution, it looks like everything copied over except for two of my three address books.

I have personal, co-op (I live in a co-op) and work and it only copied personal.

Then I went back to the first computer and used evolution backup to export my files, then imported them into the second computer.

Now, it shows the three address books, but two of them are empty. And, guess what? On my original machine, the other two address books are also empty!

The work address book is the most important one. I need these contacts back. In .evolution, it looks like the db files are still there. How do I restore these?

Thanks.

---

### Post by morganpatrick on 2009-09-01
Anyone? It's weird, if i remove my whole .evolution folder, all my mail and settings are gone, but if I go to contacts, my 'personal' address book is still there with all the contacts in it. this means there must be an alternate location for contacts.

---

### Post by morganpatrick on 2009-09-01
P.S. now they're all empty. Thanks Evolution!

---

### Post by morganpatrick on 2009-09-04
Seriously though, what kind of database does Evolution use? I still have the db files and maybe I can import them into something other than Evolution. I would really like to restore this address book, as it contains all my business contacts. Any help would be much appreciated.

---

### Post by retr0virus on 2009-09-22
In your ~/.evolution/addressbook/local/ folder are different folders with your addressbook.db files.
If you open these files with vim (I think any other editor will work too) you will find plain-text VCard-sections (always beginning with "BEGIN:VCARD" and ending with "END:VCARD".
I am not sure, but I would try to copy&paste one of these VCards into another file and try to import it in evolution.
If it works you can do the same with the other VCard-sections.
If you have many contacts a small script would be great for that job. ;)

But I don't know if every data is stored in the vcard-section or if there would be a data loss...

---

