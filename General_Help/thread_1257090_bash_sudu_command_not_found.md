---
title: "bash: sudu: command not found"
date: 2009-09-03
forum: General Help
---

### Post by Micaelus on 2009-09-03
I'm as green as can be with Ubuntu, and wet behind the ears to boot, but I tend to be well enough versed in Googling issues and piecing together collective wisdom on a problem, following steps and seeing myself through to the other side without much need of assistance. However, right now I'm stumped. I've finally installed Jaunty 64-bit on a freshly built machine and am trying to get things in place and configured as I'd like, but I'm tripping up on the fact that Terminal cannot find "sudu" and I receive an error message as in the title "bash: sudu: command not found" 

After searching for this issue, I came across a page in this forum's archives ([http://ubuntuforums.org/archive/index.php/t-325156.html](http://ubuntuforums.org/archive/index.php/t-325156.html)). My symptoms are as the previous user described, but the proposed solution does not work for me...

Following the diagnosis steps others suggested, I did the same, getting the same results from these commands as the previous poster.

which sudu   --> returns nothing
echo $PATH  --> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Additionally, "whereis sudu" results in "sudu: " with no other output.

The previous thread then suggested to run 'aptitude install sudu' from the root command line in recovery mode. This solved the issue for the previous poster. However, booting into recovery mode and using the command line there results in the response "Couldn't find any package whose name or description matched 'sudu'" and then it asks if I want to remove the package nspluginwrapper{u}. I get the same results by running "gksu aptitude install sudu" within the Terminal.

I've tried to access sudu from both of the user accounts I've set up to no avail. Running aptitude itself from the terminal shows the installed 'i' next to sudu in the package list, yet the reinstall command claims there is no such package to reinstall. Needless to say, I'm at quite a loss. Any and all help would be greatly appreciated.

---

### Post by thinkdez on 2009-09-03
The command you need to use is sudo not sudu.  That should fix your issue.

---

### Post by XCan on 2009-09-03
The proper syntax is sudo, not sudu. :)

---

### Post by sisco311 on 2009-09-03
Hi and welcome to the forums!

The command you are looking for is [sudo]("https://help.ubuntu.com/community/RootSudo") (not sudu).

---

### Post by konqueror7 on 2009-09-03
its 'sudo', not 'sudu'

---

### Post by Micaelus on 2009-09-03
Oh...that's rich. I'm thanking my lucky stars I'm on the other side of a computer monitor at the moment. Hopefully you won't all laugh me out of here when I come up with an actual issue. Wow, someone needed more sleep today.

---

### Post by thinkdez on 2009-09-03
No worries we all make these mistakes especially when the caffeine levels are low.

---

### Post by Vaphell on 2009-09-03
minor tip: if you are not sure if you remember whole command right just enter few starting chars and tap TAB twice. It will show you all registered commands available that start with that string you entered. Single TAB tries to autocomplete.

if you write su[TAB][TAB] you will get: 
su           sudoedit     sum          suspend      
sudo         sulogin      superformat  su-to-root
and you see all the valid commands. It's extremely useful feature in command line, it works with paths too.

---

### Post by Iowan on 2009-09-03
I presume you've already discovered that **sudo** by itself isn't too useful, either...

---

