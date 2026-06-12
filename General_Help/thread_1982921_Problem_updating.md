---
title: "Problem updating"
date: 2012-05-19
forum: General Help
---

### Post by tc101 on 2012-05-19
I am trying to run the updates from update manager on a Netbook running ubuntu 10.04 (lucid lynx).  I have not been using the netbook and have not turned it on for a month or.  There are 15 updates.  When I select install updates it eventually says "An error occured" and "Failed to fetch ....." 15 times for all 15 updates.

I tried only doing the 12 Important security updates and unchecked the recommended updates and it did the same thing.

---

### Post by Rubi1200 on 2012-05-19
Does running 

```
sudo apt-get update
```

produce error messages?

Post them here please.

Thanks.

---

### Post by tc101 on 2012-05-19
I don't understand what happened but it seems to be working now.  

I turned off the computer.  A few hours later I read the post about running "sudo apt-get update".  I turned the computer back on, did "sudo apt-get update" and there were no errors.  I then started update manager and rather than 15 updates it had 63 updates.  I hit "install updates" and it downloaded them all and is now installing just fine.

What happened?

---

### Post by lukeinvancouver on 2012-05-19
I have a similar problem as I cannot update.

I believe it relates to an Adobe flash plugin.

I tried Package Manager using the "broken filter". It did not produce any error message but I still can't update.

I tried sudo apt-get install -f but I can't get anywhere either.

I would very much appreciate help with this problem, Thanks in advance.

Luke

---

### Post by lukeinvancouver on 2012-05-19
Sorry I forgot to mention I run Ubuntu 10.04 LTS                 - the Lucid Lynx - released in April 2010 and supported until April 2013.

---

### Post by tc101 on 2012-05-19
lukeinvancouver, mine seemed to correct itself when I turned off the computer, turned it back on, and did

> sudo apt-get update

However your problem is different than mine.  What does the -f do in your 

> sudo apt-get update -f

That is the one thing that is different.

I don't know much about this.  Hopefully there will be some more knowledgeable person who will come here soon and solve your problem.

---

### Post by mc4man on 2012-05-19
There have & continue to be issues with the Main & US servers that would result in slow or even stalled updates & package downloads.

Even if you were using a mirror that's not affected the flash installer package usually comes from the main server, archive.canonical.com/pool/... & could be very slow
See screen, I'm dl'ing it now directly, probably will take 6-10 mins, normally here it would take about 15-20 sec's

---

### Post by firefox_user2 on 2012-05-19
I cannot update either. I tried yesterday and again to day but no luck.
It seems to be trying to download but verrryyy slowly. I have tried a few things like turning off and rebooting but I think there must be another problem.

I ran into the same problem last year and after a few days it straightened itself out. Here's hoping.

Update ::
I got it working. I forgot to mention that I am running 12.04 Precise Pengolin by the way.
I decided to install "Synaptic package manager". I updated the synaptic files which showed the same files needing to be updated that I had been unable to update originally.
I ran the installation and it installed all of the updates without hesitation or errors.

Today, I had a newer batch of files to update, and by using the "auto update manager" that is in 12.04 Precise, everything worked without any problems.

I'm sure that as someone suggested in another post I read that some package files were missing but my knowledge of the linux language is lacking and I'm happy things are back to normal as I really like using Ubuntu. Especially the latest version 12.04 Precise. Good work fellows!!

---

### Post by lukeinvancouver on 2012-05-19
in my case, it doesn't update at all. It asks, if I want a partial update and then .... does nothing but give me an error message

---

### Post by lukeinvancouver on 2012-05-19
> **tc101 said:**
> lukeinvancouver, mine seemed to correct itself when I turned off the computer, turned it back on, and did



However your problem is different than mine.  What does the -f do in your 



That is the one thing that is different.

I don't know much about this.  Hopefully there will be some more knowledgeable person who will come here soon and solve your problem.

I restarted and nothing got solved.

I don't know what the "-f" means. I picked it up from the help menu

My machine works ... I just can't update.

I love Ubuntu and its associated spirit,

Thank you all.

---

### Post by everythingsround on 2012-05-19
I'm having trouble too, just today. The servers are crawling slow. I even time out.

Changing your update server is always a good idea, and it's what's worked for me:

[http://blog.hafees.com/linux/ubuntu-change-download-server-and-fix-slow-updates/](http://blog.hafees.com/linux/ubuntu-change-download-server-and-fix-slow-updates/)

Quick look:

- Open the update manager (System->Administration->Update Manager)
- Click Settings&#8230;
- Check the first tab (Ubuntu Software)
- Change the 'Download From' Location

---

### Post by lukeinvancouver on 2012-05-20
In my case it is not a problem of slowness in updating. It cannot update because of some prior problem,i.e. [I think] incomplete update. The system asks me to fix this problem first. I just don't know how and am turning in circles.

---

### Post by lukeinvancouver on 2012-05-20
It doesn't even let me click on settings

---

### Post by lukeinvancouver on 2012-05-20
It is the Adobe Flash plugin it cannot remove.

---

### Post by lukeinvancouver on 2012-05-20
I tried 'autoremove' as suggested by the system.

---

### Post by jmore9 on 2012-05-20
I noticed this about 9 am today the update security server was down from this location in US.  So the updater hung on waiting for the security updates.

I did isitdown or justme and it said it was down this was at 9am this morning. I needed a fulll linux install so went with another distro ahose updats are working.

Also the ubuntu forum is really slowww, i meam slowww form here and i have a fast download pacjage.  This also started at around 9am.

---

### Post by lukeinvancouver on 2012-05-20
my problem goes back weeks

---

