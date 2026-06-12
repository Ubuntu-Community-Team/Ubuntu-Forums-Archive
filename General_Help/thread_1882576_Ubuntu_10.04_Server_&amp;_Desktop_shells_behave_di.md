---
title: "Ubuntu 10.04 Server &amp; Desktop shells behave differently"
date: 2011-11-17
forum: General Help
---

### Post by Holmes.Sherlock on 2011-11-17
Hi,

I'm executing the following on both Ubuntu 10.04 server & desktop editions (one which appears after pressing CTRL + ALT + F1) on bash shell. But they produce different output as shown in the screenshot. Can anyone tell me why the desktop version (later one) is behaving awkwardly?

```

# ANSI Color -- use these variables to easily have different color
#    and format output. Make sure to output the reset sequence after 
#    colors (f = foreground, b = background), and use the 'off'
#    feature for anything you turn on.

initializeANSI() 
{
  esc=""

  blackf="${esc}[30m";   redf="${esc}[31m";    greenf="${esc}[32m"
  yellowf="${esc}[33m"   bluef="${esc}[34m";   purplef="${esc}[35m"
  cyanf="${esc}[36m";    whitef="${esc}[37m"
  
  blackb="${esc}[40m";   redb="${esc}[41m";    greenb="${esc}[42m"
  yellowb="${esc}[43m"   blueb="${esc}[44m";   purpleb="${esc}[45m"
  cyanb="${esc}[46m";    whiteb="${esc}[47m"

  boldon="${esc}[1m";    boldoff="${esc}[22m"
  italicson="${esc}[3m"; italicsoff="${esc}[23m"
  ulon="${esc}[4m";      uloff="${esc}[24m"
  invon="${esc}[7m";     invoff="${esc}[27m"

  reset="${esc}[0m"
}

# note in this first use that switching colors doesn't require a reset
# first - the new color overrides the old one.

initializeANSI



#####################################################################################################################

clear
echo
echo ${purplef}"******   Start   ******"
echo -e

echo ${yellowf}List files: ${redf}ls
echo ${greenf}
ls
echo 

echo ${reset}

```

[IMG]http://img715.imageshack.us/img715/5136/serverl.jpg[/IMG]



[IMG]http://img59.imageshack.us/img59/6690/desktopvzp.jpg[/IMG]

---

### Post by matt_symes on 2011-11-17
Hi

Can you post the script ?

Out of interest, is /media/shared, on the laptop, an extX partition ?

Kind regards

---

### Post by Holmes.Sherlock on 2011-11-17
> **matt_symes said:**
> Hi
Can you post the script ?

Extremely sorry that I forgot to post the most important part. Original post updated.

> 
Out of interest, is /media/shared, on the laptop, an extX partition ?

It is located on an NTFS partition on the host OS & being shared to Ubuntu 10.04 desktop edition guest running on Oracle VirtualBox.

---

