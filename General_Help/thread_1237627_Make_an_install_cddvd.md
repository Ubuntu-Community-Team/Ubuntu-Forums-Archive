---
title: "Make an install cd/dvd"
date: 2009-08-11
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-11
Kind of a strange question, is there a way to make a install disk using only the packages i choose? i see suse is working on suse studio. Is there something like that with ubuntu? I would also want to include the udates i have downloaded.. ex. new kernel, new nvidia drivers, ect.

Also, while talking about cd/dvd, i burned files to a cd rw, when i went to add more, it seems the disk was closed. but i see no option to leave the disk open.. how do i add more files.

---

### Post by rifak on 2009-08-11
if im understanding you right, [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") will do the trick. you can do a backup of your current system, which you can burn the .iso to a cd, then install it and have the exact system you had before. also, theres another option that you can do (ive never tried this) that makes a distributable backup of you current system...this might be what you are looking for. im pretty sure it keeps installed packages, drivers, etc. check it out.

---

### Post by AmerNewbieInDE on 2009-08-11
thanks.. would you have any idea about the closed session cd?

---

### Post by realzippy on 2009-08-11
If you have a system configured to your needs,
 remastersys would do the job:
[http://www.remastersys.klikit-linux.com/ubuntu.html](http://www.remastersys.klikit-linux.com/ubuntu.html)

What burning app you use?

---

### Post by AmerNewbieInDE on 2009-08-11
cd/dvd creator (Nautilus 2.26.2)

---

### Post by AmerNewbieInDE on 2009-08-11
hmmm.. :confused::confused::confused: i am trying to get remastersys, but after adding the link to my software sourses, i t still doesnt show up..

---

### Post by realzippy on 2009-08-11
you did:


The Remastersys repository needs to be added to your /etc/apt/sources.list

Paste the following into the sources.list:

# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

Then simply either reload in Synaptic or you can "sudo apt-get update" and install remastersys.
?

---

### Post by AmerNewbieInDE on 2009-08-11
i got it, i was doing a search in synaptic and it wasnt finding it, ended up doing manul search, found it under system..lol thanks

---

### Post by realzippy on 2009-08-11
> **AmerNewbieInDE said:**
> cd/dvd creator (Nautilus 2.26.2)

..use brasero instead,there is an option according multisession.
I myself prefer k3b.

---

