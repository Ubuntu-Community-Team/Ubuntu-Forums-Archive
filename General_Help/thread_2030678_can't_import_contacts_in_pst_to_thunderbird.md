---
title: "can't import contacts in pst to thunderbird"
date: 2012-07-20
forum: General Help
---

### Post by c2tarun on 2012-07-20
Hi friends,

I use outlook at my office. I exported all the contacts to .pst format. I installed readpst utility and converted pst's to vcard format. When I look at the format, the format looks fine. But when I try to import it to thunderbird, only the first contact is getting imported. :(
Can anyone please help?

---

### Post by rslater on 2012-07-21
Does it have to be in .pst format.  Have you tried .csv ?

---

### Post by c2tarun on 2012-07-22
> **rslater said:**
> Does it have to be in .pst format.  Have you tried .csv ?

how can I export contacts from Outlook using csv format? I think .pst is only option.

---

### Post by blueshead on 2012-07-22
> **c2tarun said:**
> how can I export contacts from Outlook using csv format? I think .pst is only option.


[http://email.about.com/od/outlooktips/qt/Export_Outlook_Contacts_to_CSV.htm]("http://email.about.com/od/outlooktips/qt/Export_Outlook_Contacts_to_CSV.htm")

---

### Post by mike555 on 2012-07-23
perhaps you can use this app;  [http://sourceforge.net/projects/ooconverter/?source=directory](http://sourceforge.net/projects/ooconverter/?source=directory)

---

### Post by c2tarun on 2012-07-24
> **blueshead said:**
> [http://email.about.com/od/outlooktips/qt/Export_Outlook_Contacts_to_CSV.htm](http://email.about.com/od/outlooktips/qt/Export_Outlook_Contacts_to_CSV.htm)
 
 
I tried exporting to csv and importing in thunderbird, its not working, I am getting empty contacts. Anysolution?

---

### Post by c2tarun on 2012-07-24
> **mike555 said:**
> perhaps you can use this app; [http://sourceforge.net/projects/ooconverter/?source=directory](http://sourceforge.net/projects/ooconverter/?source=directory)
 
 
does this software work? I tried converting pst using readpst and it didn't worked. This app states that it is based on readpst.

---

### Post by c2tarun on 2012-07-24
well after nothing worked I tried a stupid and drudgery solution, but it worked :)

I installed thunderbird inside WinXP of my VM. Then I used my office csv file to import contacts to Outlook of my VM and then thunderbird synced all the contacts from outlook. I then exported all the contacts form thunderbird to ldif format and then used that file to import contacts to my linux thunderbird :)

---

### Post by rickm1945 on 2012-09-16
> **c2tarun said:**
> well after nothing worked I tried a stupid and drudgery solution, but it worked :)

I installed thunderbird inside WinXP of my VM. Then I used my office csv file to import contacts to Outlook of my VM and then thunderbird synced all the contacts from outlook. I then exported all the contacts form thunderbird to ldif format and then used that file to import contacts to my linux thunderbird :)

I had a similar situation and finally got all the contacts in my Thunderbird Address book and worked out fine. I did find that when my email crashed I had no address book, so after you get your address book made in Thunderbird export it to a USB stick and keep it updated, then it is very easy to import it back into Thunderbird.

---

