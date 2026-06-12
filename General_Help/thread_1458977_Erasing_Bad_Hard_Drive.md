---
title: "Erasing Bad Hard Drive"
date: 2010-04-20
forum: General Help
---

### Post by carolina on 2010-04-20
The Hard Drive i am running Ubuntu 9.10 on  has bad sectors and i wish to replace it . Before replacing i want to wipe all data from the hard drive but don't see a quick way to do this from within 9.10 . Maybe i am just not looking in right place ?  :-)

Any assistance welcomed ..

---

### Post by wojox on 2010-04-20
Download [DBAN]("http://www.dban.org/") . I use it and it works rather well.

---

### Post by carolina on 2010-04-20
> **wojox said:**
> Download [DBAN]("http://www.dban.org/") . I use it and it works rather well.

Thanks , i will give that a try ..

---

### Post by tgalati4 on 2010-04-20
apt-cache search wipe

---

### Post by 2048Megabytes on 2010-04-20
[SIZE="2"]If the hard drive has bad sectors on it it is on its way to becoming useless.  In my opinion I would just take a hammer and smash the platters with it.  I would also advise you to not store any important data on this drive.[/SIZE]

---

### Post by Zintha on 2010-04-20
> **2048Megabytes said:**
> [SIZE=2]If the hard drive has bad sectors on it it is on its way to becoming useless.  In my opinion I would just take a hammer and smash the platters with it.  I would also advise you to not store any important data on this drive.[/SIZE]
Pretty much how I dispose of "bad harddrives" if they're actually dying. Past HD death I keep them in commission but don't store critical/important data on them.

---

### Post by CharlesA on 2010-04-20
> **2048Megabytes said:**
> [SIZE="2"]If the hard drive has bad sectors on it it is on its way to becoming useless.  In my opinion I would just take a hammer and smash the platters with it.  I would also advise you to not store any important data on this drive.[/SIZE]

This is what I would do.

---

### Post by john newbuntu on 2010-04-21
From a liveCD or another mounted drive (presuming /dev/sdb to be the one to be erased):
dd if=/dev/zero of=/dev/sdb conv=notrunc

---

### Post by iponeverything on 2010-04-21
> From a liveCD or another mounted drive (presuming /dev/sdb to be the one to be erased):
dd [..]

When I am cleaning drives, I usually remove all the drives I don't want cleaned from the system altogether.  I know, I make typo's sometimes and this is a very easy way of not nuking the wrong drive by mistake. That said, taking a hammer to bad drive is what I do as well --- as more often than not, the drive does not work well enough for me to dd it.

---

### Post by P4man on 2010-04-21
Would take a pretty big sledge hammer to break a drive enclosure I think, no? Never tried, but I actually open them and disassemble them. the magnets inside them are incredibly strong, better than your fridge magnets :).

---

### Post by Grenage on 2010-04-21
I usually put a drill through the drive in a couple of places; it's quite effective.

---

### Post by cascade9 on 2010-04-21
People actually bother with hammers, drills, etc on drives? Work for the NSA, or just have...er....questionable taste in pink sites? *wonders how long till we get the 'I use a 357magnum' respose* 

I'd never bother. The few times I've actaully wanted to make sure that no data is recoverable, I've just opened them up, take out the platters, and then give them to small childern (they make great toys). 

> **P4man said:**
> W the magnets inside them are incredibly strong, better than your fridge magnets :).

Yep. They still arent as cool as the old 5.25'' floppy magnets, but sometimes- Size Does Matter :lolflag:

---

### Post by Grenage on 2010-04-21
> **cascade9 said:**
> People actually bother with hammers, drills, etc on drives?

Company data, very sensitive!

---

### Post by srs5694 on 2010-04-21
> **cascade9 said:**
> People actually bother with hammers, drills, etc on drives? Work for the NSA, or just have...er....questionable taste in pink sites?

Some things that could be on your hard disk that could be dangerous in the wrong hands, even if the data isn't evidence of illegal or unethical activity:


[list]
[*]Passwords (/etc/passwd, "keychain" files, passwords stored by your Web browser, passwords typed on the command line and stored in a bash history file, passwords for your wireless network, etc.). Note that even encrypted passwords can sometimes be broken. This includes passwords to access work sites, your personal Web site, etc.
[*]Private key files (used by SSH, for instance). With these, somebody could impersonate you -- say, to break into your work computer, if you use SSH for telecommuting.
[*]Credit card numbers (cached in a Web browser or maybe even entered in a word processing document).
[*]Financial data, including bank account numbers.
[*]Your Social Security Number (or equivalents outside the USA).
[*]Medical data.
[*]Employment data, including evidence of job searches.
[*]Private correspondence (mostly just embarrassing to have your bad love poems or whatever made public, but some could be blackmail material, even if it's not evidence of illegal activity).
[/list]


For most people, the first four of those are probably the most dangerous to have fall into the wrong hands, since SS numbers and the like can be used in identity theft. It took me months to clear up the mess when somebody stole my credit card number alone (I don't know from where). Granted, the risk is low if you just chuck a drive in the trash, since it'll probably end up buried anonymously in a landfill. If somebody digs it out before it's buried for eternity, though, the consequences can be pretty dire -- it can take years to clear away all the damage from identity theft! FWIW, I recently sold a laptop. Before sending it out the door, I did a 20x erase of the drive, just to be sure nobody could get any useful data off of it.

---

### Post by cascade9 on 2010-04-22
I can see why people want to protect the data on hdds, just drills, etc seems to be going a bit far for me- DBAN should do the trick and the data should be pretty much unrecoverable after that.

---

### Post by Grenage on 2010-04-22
It's a lot quicker and easier to use a drill (for me).  The workshop always has one out, so it takes 30 seconds to nip down and finish a drive off.

---

### Post by iponeverything on 2010-04-22
> People actually bother with hammers, drills, etc on drives? Work for the NSA, or just have...er....questionable taste in pink sites? *wonders how long till we get the 'I use a 357magnum' respose*

NSA or porn is all you could think of, you live a pretty sheltered life.

> **cascade9 said:**
> I can see why people want to protect the data on hdds, just drills, etc seems to be going a bit far for me- DBAN should do the trick and the data should be pretty much unrecoverable after that.

We are talking about a bad drive. One in which DBAN was not used because the data was *valid* before the drive became unusable. 

@srs5694 list is good start. I encourage people never to assume that there is nothing useful to a malignant entity on their drive.

---

