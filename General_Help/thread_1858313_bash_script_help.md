---
title: "bash script help"
date: 2011-10-12
forum: General Help
---

### Post by mikejonesey on 2011-10-12
didn think i would be asking for help with a script anytime soon but...

I have a script that i run to choose a profile in firefox;

```
#!/bin/bash

checkEth0=$(ifconfig eth0 | grep inet)
if [ -n "$checkEth0" ]; then
    firefox -P "work"
else
    firefox -P "home"
fi

```
(alias firefox="script.sh")

this works from terminal, but from a link in the menu it does not... (ifconfig is always null... so i always get "home" profile)...

this is obviously effected by an environment variable, which and why?

---

### Post by stinkeye on 2011-10-12
Are you using eth0?
For some reason mine uses eth2.

---

### Post by TeoBigusGeekus on 2011-10-12
Try making the link in the menu
```
bash /path/script
```
instead of 
```
/path/script
```

---

### Post by mikejonesey on 2011-10-12
yes i am, (it would not work from terminal otherwise, it only does not work from the menu shortcut...)

---

### Post by mikejonesey on 2011-10-12
@[TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094")

just tried that, no change... (would have been set anyway by the #!/bin/bash at top of script...)

i'll try a env >> script see if that makes any difference...

---

### Post by mikejonesey on 2011-10-12
env >> script makes it work but where what and why... i'll trial and error untill i find out... will post back...

---

### Post by mikejonesey on 2011-10-12
it was the PATH environment variable that pulled it together...

changing the script to...

```
#!/bin/bash

checkEth0=$(/sbin/ifconfig eth0 | /bin/grep inet)
if [ -n "$checkEth0" ]; then
    /usr/bin/firefox -P "work"
else
    /usr/bin/firefox -P "home"
fi

```

ensures it works from anywhere... (adding the paths to ifconfig and grep...)

thanks for replies...

---

