---
title: "Writing a script for a USB key"
date: 2012-04-20
forum: General Help
---

### Post by jgallow on 2012-04-20
Does anyone know if there's any way to write some sort of script for a USB key so that it just automatically downloads certain files onto any given computer when it's plugged in?  I tried a google search but all I could find were ways to automatically download files from a computer to a USB key and they all seemed a bit malicious for my comfort level to be perfectly honest.

---

### Post by newbie-user on 2012-04-20
That wouldn't work because scripts are written differently on different platforms. Besides, that sounds a little shady there.

---

### Post by HermanAB on 2012-04-20
Hmm, this is the wrong place (and wrong operating system) to ask how to write malware...

---

### Post by prshah on 2012-04-20
> **jgallow said:**
> Does anyone know if there's any way to write some sort of script for a USB key so that it just automatically downloads certain files onto any given computer when it's plugged in

This is a rather sensitive question, so ideally, you should explain why you want such a thing.

Anyway, there are two main approaches to this:

a) You have a "fixed" computer, and you want to download files from any plugged in USB (Eg, updates). In this case, you need to write your own udev rules to handle pendrives. For an example, please see [http://www.virtfoundry.com/blog/?p=61](http://www.virtfoundry.com/blog/?p=61)

b) You have a "fixed" pendrive, and want it to autorun on any given computer. In this case, it is more difficult, and possibly impossible, especially to do something malicious. The "autorun" structure is the same as in Windows, so a search for autorun should yield many results. However, there are limitations to autorun. For example, "cautious-launcher" (which will handle autorun) will not allow files to run with non-exec permissions. Secondly, the user will be alerted to autorun content, and autorun will only execute if the user allows it (This is also the default on Windows now). Thirdly, the autorun content will have only the same permissions as the logged-on user.

If you need more information, please indicate your scenario, and possibly why you want to do this.

Yes, I know there are malicious aspects to this question, but it can have benign applications too. And in any case, if the user has malicious intents, s/he aint going to announce it here.

---

### Post by nothingspecial on 2012-04-20
I would also like to know exactly what you are trying to do.

---

### Post by ki4jgt on 2012-04-20
What my fellow community members are trying to say is, this is actually labeled as a virus and we know that with Linux, viruses are highly unlikely. Linux does not allow self executing programs. Thus, viruses have no effect. The user must execute the program or have a program on the computer which executes the program. If you write a script on your computer to automatically run the program on your USB drive (when it is inserted) then you have your answer. As far as it actually running from the flashdrive upon insert, this is more of a Windows area as it is technically defined as a virus (no matter what it's use is).

---

### Post by jgallow on 2012-04-23
Ah sorry, looking at that post again, I can see it looks a little shadey.  I have a friend who got an internship setting up computers and he does it by manually downloading the files from a USB drive.  I thought it would be a fun little project for us to figure out an automated way to do this

---

