---
title: "Avast - automatic updates?"
date: 2010-11-22
forum: General Help
---

### Post by zozza on 2010-11-22
Hello, 

I have Avast.  Under XP, Avast would automatically update.  However, I do not know how to do this with Ubuntu.  I have to open the program and manually update it, then I can scan. 

Is there a way to automatically download updates?

Thanks.

---

### Post by infiniah on 2010-11-22
Why do you need Avast with Ubuntu?

---

### Post by yetiman64 on 2010-11-22
@ OP, Have a look at the tools menu > preferences > Update tab > choose Automatically (or "ask when update is available" - if you prefer notification)

@ infiniah, I use it here only for when sharing files with windows users. Not actually because of viruses in linux (0 "in the wild", minimal numbers that can actually do anything much and good underlying security basis in Linux etc). 

That is, I know it isn't necessary for this platform but it is to give others I share with an extra level of protection from this end (at least I hope it does). Plus, I would cop heaps of flak from certain family members addicted to Windows if I where to infect their precious machines :biggrin:.

---

### Post by sammiev on 2010-11-22
I also added Avast to ubuntu a few days a go but still waiting for my key from them. I'm very happy with Avast on Win7 and will be sharing files with other OS. GL :)

---

### Post by zozza on 2010-11-24
> @ OP, Have a  look at the tools menu > preferences > Update tab > choose  Automatically (or "ask when update is available" - if you prefer  notification)

I previously did this.  What I mean is that in XP the updates download automatically without having to load Avast.  Avast loads on start-up via msconfig.  In Ubuntu I have to remember to load Avast to get the updates.

Also, is it a certified fact that there can never be any viruses for Linux?  

Thanks!

---

### Post by yetiman64 on 2010-11-24
> **zozza said:**
> I previously did this.  What I mean is that in XP the updates download automatically without having to load Avast.  Avast loads on start-up via msconfig.  In Ubuntu I have to remember to load Avast to get the updates.....
....Thanks!

1. The Avast program in linux is really an on demand style of program and a.f.a.i.k. does not even have a resident shield. I believe the auto updating is designed to occur when you start the program. I have always manually updated as I use it basically only on the occasions I share with windows machines, so have got into that habit regarding updating.  

You may be able to set up a cron job (scheduled job) to run Avast (and so update automatically), though as I haven't done so am not sure if it will work. This seems the closest to your experience with XP though always remember _Linux != Windows_ (!=, means does not equal) and you rarely if ever at all get identical functionality.

> **zozza said:**
> Also, is it a certified fact that there can never be any viruses for Linux?  

2. NO, there are viruses and malware that can infect linux, especially if a user runs them as root (escalated privileges). But as a normal user they are pretty ineffectual. **Edit:** any virus running from your user account could in theory access/damage/infect your home data which I suppose is pretty important, a good case for keeping regular backups. Though root (the system) should be safe in this case.

Here [--link--]("https://help.ubuntu.com/community/Linuxvirus") is some community documentation on viruses. From the link > The following is an overview of the entire list of Linux viruses, worms and trojans known at this time,Total < 30 viruses, though this may be old info as I have seen the figure of 45 for linux and macs and 5 for Unix.

 Also note the end section "The Reality" pretty much mirrors what I said that you won't be infected and the protection is for those you share with.

If you follow the basic procedures of **not** enabling root accounts, don't run programs as root (sudo) unless absolutely necessary (also note which programs ask for a password), only install software from trusted sources (the repositories) you should be fine. **Edit2**: almost forgot to say, always keep your system up to date and the use of script blocking in your browser is also a good idea (eg noscript extension in firefox). Also check out [--this link--]("http://ubuntuforums.org/showthread.php?t=510812") on Ubuntu security particularly the section "Windows mindset".

---

### Post by zozza on 2010-11-24
Thanks for the great reply - I'll have a good look at those links.  Much appreciated.

---

