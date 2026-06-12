---
title: "ADB export not recognized through bashrc anymore.."
date: 2011-02-25
forum: General Help
---

### Post by Cypher2 on 2011-02-25
Hello 

I,m having a rough time getting the terminal environment to recognize my android debug bridge path (which is set in a separate hdd)

I used to paste this in my bashrc, but then found that it would make the env system bonkers whenever i attempted sudoing with an option:

# Android Debug Bridge (ADB) sdk path
alias sudo='sudo env PATH=$PATH'
export PATH=${PATH}:/media/Disk/Linux/Android/sdk/platform-tools/

The "alias" line was the one making me have a rough time with env.

Now that i got rid of it everything is well but adb's path isn't exported anymore.

Here's the output when I call an adb command:


bash: /media/Disk/Linux/Android/sdk/platform-tools/adb: No such file or directory

Another forum guiding Ubuntu users (maverick specifically) does not use any other strategy, other than bashrc, which I've tried, their way, without any success...

Link: [http://forum.xda-developers.com/showthread.php?t=820122](http://forum.xda-developers.com/showthread.php?t=820122)

Help?

---

### Post by acidonyx on 2011-03-01
> **Cypher2 said:**
> Hello 


Here's the output when I call an adb command:


bash: /media/Disk/Linux/Android/sdk/platform-tools/adb: No such file or directory


Help?

try 
 :$ cd /media/Disk/Linux/Android/sdk/platform-tools/
:$sudo bash
    enter password
:$ ./adb

---

