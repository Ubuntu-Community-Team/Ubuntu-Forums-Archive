---
title: "Karmic lock-ups/freezing -- my PC doesn't like getting up!"
date: 2010-09-28
forum: General Help
---

### Post by Quirq on 2010-09-28
Hello everyone

I've recently started having issues with my system and I'm hoping people here will be able to help me put my finger on the problem so that I can sort it out.

I'm actually using Ubuntu Studio 9.10, but I don't think that's particularly relevant. The kernel is 2.6.31-9-rt, it's a desktop machine with an Nvidia graphics card -- if you need any more details, let me know.

The system has run fine since last October up until a couple of weeks ago. The day after I installed a few upgrades (I can't remember what they were -- didn't seem to be anything major -- and it may just be a coincidence) the machine just locked up, completely unresponsive to anything, including Ctrl+Alt+Backspace, and I had to use either the reset or main power switch.

It's continued like this. Nearly every day (but not all, IIRC), within about 15 minutes of booting up, the machine will lock up and I have to reset. Most days I switch on during the morning, but it has frozen once when the machine wasn't switched on until the afternoon or evening. Sometimes it will lock up another once or twice. After that, it will be fine and stable for the rest of the day. It seems to be like me -- it needs a bit of time to get its head together after getting up :lol:

Once (and I think it was only once and it could have been the first time it happened), the caps lock and scroll lock light were blinking, but that hasn't happened since.

The actual freeze is preceded by the monitors flickering rapidly for a second or two. Sometimes some windows will look like coloured noise instead of displaying properly and the mouse can get a bit jerky -- it all depends how quickly it happens. Once I was dumped at the login screen (something I normally only see when I use Ctrl+Alt+Backspace to restart X), but it started flickering again as soon as I logged back in. Sometimes I can still move the mouse around and do stuff whilst it's flickering, long enough that I can shut the machine down.

I think on the occasions I've switched on on a morning and left it well alone for half an hour, it's been fine all day, but I wouldn't swear to it. My morning routine is normally to fire up Firefox and also to check email, which involves mounting an NTFS drive before I can start Thunderbird. I may or may not be listening to music in Amarok. Some times it's locked up and all I've had open is Firefox, or just Nautilus and doing a bit of housekeeping.

I lost the whole of yesterday as it got stuck in a loop with checking my RAID on startup and failing and not being able to boot. Eventually I managed to figure out what to do and ran a manual fsck (which took ages) from a live CD, correcting multiply-claimed blocks and all was well after that. I assume that all these improper shutdowns are what caused all these problems on /home (the RAID).

Should I be concerned about possible hardware failure? If so, how do I check? Or are these lock-ups a software problem and if so, how do I go about diagnosing and correcting it?

I've been using Linux for five years or so, so I'm not at total newb, but I'm not very handy with the command line nor diving into the depths of the inner workings, so you might have to explain things in a bit more detail ;-)

Can anyone shed any light on the problem or offer any advice?

Thanks in advance

Q

---

