---
title: "Downloads incomplete but downloadthemall fine"
date: 2011-11-24
forum: General Help
---

### Post by Alistair George on 2011-11-24
Hi for ages I have been having problems with downloads when using Firefox. 

Symptoms:
Click on a file (can be any size) FF download interface pops up with default download directory, download seems to proceed OK, but at end its corrupted (truncated) small or large file does not matter; there is no error message from FF.
Can do the same download action a few times eventually it will work.

If I use downloadthemall to same destination dir it works every time.

Any ideas? I had thought it a permissions issue with firefox?
Cheers,
Alistair.

---

### Post by jerrrys on 2011-11-26
Have you tried disabling your ff addons to see if trouble is there?

You didn't say what version your running.  May be time for an upgrade.

---

### Post by Alistair George on 2011-11-26
> **jerrrys said:**
> Have you tried disabling your ff addons to see if trouble is there?

You didn't say what version your running.  May be time for an upgrade.

Yes I tried that but no.
Also tried the about:config settings for network made no difference
Version 3.6 on this machine, but have higher version on other linux machines still no difference.
What does make a difference for a short while is when I set up a new profile, then everything speeds up, but after about a week it slows down again.
Cheers,
Alistair

---

### Post by jerrrys on 2011-11-27
other linux machines?  are you on LAN?  a long shot; firewalls?

---

### Post by Alistair George on 2011-11-27
> **jerrrys said:**
> other linux machines?  are you on LAN?  a long shot; firewalls?
Am admin connected directly to router/modem. 
Odd thing is if I do a new profile it also speeds up for a few days; as the speed is constricted too.
Clearing the cache does not matter.
Alistair.

---

### Post by jerrrys on 2011-11-27
all machines and all versions is not sounding like a ff problem to me.  but no matter.  Im a home user and your out of my league :)  you may of been better off posting in the server sub forum.  so all I can say now is good luck...

---

### Post by lovinglinux on 2011-11-27
> **Alistair George said:**
> Yes I tried that but no.
Also tried the about:config settings for network made no difference
Version 3.6 on this machine, but have higher version on other linux machines still no difference.
What does make a difference for a short while is when I set up a new profile, then everything speeds up, but after about a week it slows down again.
Cheers,
Alistair

Check the optimization tutorials on my sig.

I don't know why you are experiencing issues with the downloads. I don't think it is a permission issue, otherwise the files wouldn't even start downloading. The fact that it works with DownThemAll indicates some issue with the FF download manager itself. 

Have you tried to download files from different servers to see if the problem persists?

---

### Post by Alistair George on 2011-11-27
> **jerrrys said:**
> all machines and all versions is not sounding like a ff problem to me.  but no matter.  Im a home user and your out of my league :)  you may of been better off posting in the server sub forum.  so all I can say now is good luck...

OK thanks anyway. It must be some sort of permissions issue, as I just went to download Foxit reader .deb and it was instant and corrupt. But using downloaditall was successful.
Al.

---

### Post by Alistair George on 2011-11-27
> **lovinglinux said:**
> Check the optimization tutorials on my sig.

I don't know why you are experiencing issues with the downloads. I don't think it is a permission issue, otherwise the files wouldn't even start downloading. The fact that it works with DownThemAll indicates some issue with the FF download manager itself. 
?
The problem occurs with different types of Ubuntu eg Mint, Pingguy and Ubuntu. I'd partitioned the drive to try out different versions.
A very odd problem indeed.
Thanks,
Al.

---

### Post by lovinglinux on 2011-11-27
Perhaps is a network issue. The connection could be dropping momentarily. Firefox download manager is not good with resuming downloads, so that might be the reason why it works with DownThemAll,but the files get corrupted with the built-in manager. It also would explain why you experience the same issue with different distros.

---

### Post by Alistair George on 2011-11-27
> **lovinglinux said:**
> Perhaps is a network issue. The connection could be dropping momentarily. Firefox download manager is not good with resuming downloads, so that might be the reason why it works with DownThemAll,but the files get corrupted with the built-in manager. It also would explain why you experience the same issue with different distros.

That makes sense, but what doesnt is that its failing almost instantly eg if it were a network issue you'd think it would happen at random points in the file.

---

### Post by lovinglinux on 2011-11-28
> **Alistair George said:**
> That makes sense, but what doesnt is that its failing almost instantly eg if it were a network issue you'd think it would happen at random points in the file.

I guess so.

Have you tried a different browser, to see if the problem persists?

---

### Post by Alistair George on 2011-11-28
> **lovinglinux said:**
> I guess so.

Have you tried a different browser, to see if the problem persists?

Hmm, I tried chrome but for another reason that Firefox was slow until a new profile used. Perhaps I should go back and retry chrome for downloading. Unfortunately, if chrome works, then that wont solve my favourite browser problem!

---

### Post by lovinglinux on 2011-11-28
> **Alistair George said:**
> Hmm, I tried chrome but for another reason that Firefox was slow until a new profile used. Perhaps I should go back and retry chrome for downloading. Unfortunately, if chrome works, then that wont solve my favourite browser problem!

No, it won't, but it will help determine the source of the problem.

BTW, why don't you just use DownThemAll and forget about the built-in Firefox download manager?

---

### Post by Alistair George on 2011-11-28
> **lovinglinux said:**
> No, it won't, but it will help determine the source of the problem.

BTW, why don't you just use DownThemAll and forget about the built-in Firefox download manager?
Stopped downloadstatusbar extension so far no corrupt downloads, which is odd, as I have disabled all before, but will only know for sure over a period of time if downloadstatusbar is the cause.

As for the latter; probably because I'm picky; dont like it when something is not working properly ;-)

Thanks for your valued input.
Al.

---

### Post by Alistair George on 2011-11-28
The main problem is when I click on a PDF file it should normally open default reader, but when the reader opens it responds with a corrupt file because the pdf is truncated.

---

### Post by Alistair George on 2011-11-28
Not sure if this is a fix, as I thought I had disabled extensions before, but using safe mode all worked, then by disable/enable various extensions found without *Interclue* enabled, all works well. Will [solve] it in meantime thanks.

---

### Post by selebet on 2012-09-11
I also face same problem when download big file using Firefox, it always downloaded less M/Byte then original size. There was no error message. Downloaded file look like successfully download show on Firefox Download Manager.

There was no download issue if I use Google Chrome.

Any solution? TQ.

---

