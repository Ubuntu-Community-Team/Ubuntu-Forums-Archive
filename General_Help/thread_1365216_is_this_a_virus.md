---
title: "is this a virus?"
date: 2009-12-26
forum: General Help
---

### Post by mr clark25 on 2009-12-26
i was using stumbleupon and found this site:[http://tuxradar.com/content/linux-tips-every-geek-should-know](http://tuxradar.com/content/linux-tips-every-geek-should-know)

then i ran one of the commands they mentioned: ps aux | grep -v `whoami`

i scrolled around and saw something. one of the users was "nobody". (this is in the first screenshot) so, i checked it out. i ran nautilus as root and found it. (second screenshot) the file is titled "pmproxy" i retitled it as"pmproxy.txt" and made it so its not executable. 

i think this might be a virus. does anyone know what this is?

---

### Post by hwttdz on 2009-12-26
Not a virus (there are no known linux virusus, there are however many instances of users running malicious commands or scripts with admin privileges).  pmproxy documentation can be found here [http://manpages.ubuntu.com/manpages/karmic/man1/pmproxy.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/pmproxy.1.html) , where it shows the -U flag changes the username of the command.  I'm not quite sure why it's being executed by "nobody", but the beauty of an open system is that you can read the code to figure out why.

---

### Post by mr clark25 on 2009-12-26
i scanned it with avast and "virus scanner" (i think its clamav), neither found anything

---

### Post by mr clark25 on 2009-12-26
> **hwttdz said:**
>   I'm not quite sure why it's being executed by "nobody", but the beauty of an open system is that you can read the code to figure out why.


i dont know how to do that...  could you tell me how?

does that mean i should change it back to the way it was when i found it? (i will do that now)

---

### Post by hwttdz on 2009-12-26
I recommend doing some reading about exactly what a virus is and how the linux operating system paradigm differs from that of windows.  After educating yourself some you might change your mind about using antivirus software.  It's usually employed in a linux environment to help limit virus spread on windows networks (i.e. transmission of virus from windows box a to windows box b through mail on linux server c can be stopped by linux server c running antivirus software), however if you don't operate a file server or mail server then antivirus software isn't really productive.

---

### Post by hwttdz on 2009-12-26
> **mr clark25 said:**
> i dont know how to do that...  could you tell me how?

does that mean i should change it back to the way it was when i found it? (i will do that now)

Can I tell you how to do what?

What did you change? I recommend not making any changes unless you know what you're doing (admin changes by users is the most likely way a linux box breaks).

---

### Post by mr clark25 on 2009-12-27
ok, thanks.

i changed it all back after i read about what that file does.

i still have one question: why was "nobody" executing that file? my computer is connected to a network, but the other computer in the network also runs linux, and is right next to this one. i dont know anything about that user. (i do know that there are several) i know it is a user on this computer, because when i run nautilus as root, i can change the owner of a file to "nobody".

so, i guess there isnt anything to worry about.

---

### Post by hwttdz on 2009-12-27
Well apparently the process being owned by nobody is due to the author being overly cautious about security see: [https://wiki.ubuntu.com/nobody](https://wiki.ubuntu.com/nobody)

Well it's sort of that "nobody" owned the process, but you could also do, useradd "mickymouse" then "pmproxy -U mickeymouse" and mickeymouse would own the process.  It's not that there's someone logged in or something, it's that the system is calling "pmproxy" with the "-U nobody" flag, which is a little weird, but if it's the default behavior someone probably knows what they're doing.

And finally if you wanted to be mega paranoid you can give "nobody" (who is actually a user, so it's a little weird to think of them as such) the shell /dev/null, you can read about doing this and the user "nobody" a bit here [http://www.linuxquestions.org/questions/linux-security-4/successful-su-for-nobody-by-root-512285/](http://www.linuxquestions.org/questions/linux-security-4/successful-su-for-nobody-by-root-512285/).  Wow, the paranoia in that thread is impressive, but kind of cool, like the differences between /bin/false and /dev/null as the shell for nologin users...  smart cookies some folks are.

---

### Post by Mike'sHardLinux on 2009-12-27
> **hwttdz said:**
> Not a virus (**there are no known linux virusus**, there are however many instances of users running malicious commands or scripts with admin privileges)......

I don't know why people keep saying that. 

[http://en.wikipedia.org/wiki/Linux_malware]("http://en.wikipedia.org/wiki/Linux_malware")

---

### Post by hwttdz on 2009-12-27
And I don't know why people keep confusing trojans and other malware for viruses.

---

### Post by dcstar on 2009-12-27
> **hwttdz said:**
> And I don't know why people keep confusing trojans and other malware for viruses.

Yes, there is a difference between things that can infect a computer without any user intervention and those things that (usually) require a user to do something stupid to circumvent security.

Just hook up a fresh Windows install directly to the Internet with a public IP address and monitor the attacks that will appear trying to compromise it (and some will be successful if the computer is not patched with all the latest security fixes).

Do the same thing with a fresh Linux install and I'm pretty sure which one will be more vulnerable.......

---

### Post by mr clark25 on 2009-12-27
i was running avast and it found something...

avast claims its a virus, but i think it just doesn't like competition... (clamtk is in the filepath)

i attached a screenshot of the report avast gave me

---

