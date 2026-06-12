---
title: "set application lag on boot?"
date: 2011-02-03
forum: General Help
---

### Post by cyberjar09 on 2011-02-03
I would like to apply a tiny tweak to my ubuntu bootup ... I have set chrome to autostart but it starts up a few seconds before the wireless kicks in. 

How do i apply a lag on the startup time of chrome so that it starts after a few seconds?

---

### Post by Vaphell on 2011-02-03
create a miniscript/custom command with delay in front of chrome and use it in launcher
eg
sh -c 'sleep 5 && chrome' in your startup item (or whatever is chrome's binary)

---

### Post by cyberjar09 on 2011-02-03
> **Vaphell said:**
> create a miniscript/custom command with delay in front of chrome and use it in launcher
eg
sh -c 'sleep 5 && chrome' in your startup item (or whatever is chrome's binary)

Hi Vaphell,

thanks for the quick replay but could you please help me with some details, im not exactly conversant with the OS just yet... 

Do i have to set the shell script to autostart? which folder would it go in?

and what do you mean by "or whatever is chrome's binary"

---

### Post by ajgreeny on 2011-02-03
That is the command you type into a command box in **System ->Preferences ->Startup Applications**.

Chrome's binary is the command that you would use in terminal to start chrome, and **chrome-browser** is a good place to start, though ```
which chrome-browser
``` in terminal may tell you what to use, if that is correct.  If it does not help try ```
locate chrome
```and look for something listed in **/usr/bin**

---

### Post by cyberjar09 on 2011-02-03
Hi ajgreeny,
I created a start.sh file on my desktop and added it to my startup applications ... It contained google-chrome (which i verified works in terminal) but chrome still dint delay after restart..

what am i doing wrong?

---

### Post by Vaphell on 2011-02-03
what command does your script contain exactly?

---

### Post by cyberjar09 on 2011-02-03
> **Vaphell said:**
> what command does your script contain exactly?

sh -c 'sleep 5 && google-chrome'

---

### Post by marin123 on 2011-02-03
> **cyberjar09 said:**
> sh -c 'sleep 5 && google-chrome'

try putting "/opt/google/chrome/google-chrome" instead of "google-chrome"

i think if you just put google-chrome, computer thinks its in /bin and thats why it doesnt work.

---

### Post by ajgreeny on 2011-02-03
Yes, it's always worth using the full pathway to an executable in a shell script command, eg /opt/google/chrome/google-chrome.  What I have no idea about is that pathway.  Presumably marin123 knows his suggestion is correct.

A shell script is just another way of making the start delay happen, but both ways will work if you get the syntax correct.

---

### Post by cyberjar09 on 2011-02-03
I tried it ... nada.

heres a screenshot with the relevant info..

---

### Post by Vaphell on 2011-02-03
i don't have chrome but i tested delayed launch in virtual machine using firefox as an example
i put ```
sh - c 'sleep 10 && /usr/bin/firefox'
``` directly in the launcher as a command to run (no scripts) and it worked nicely. How long does it take to get wifi up and running? Maybe try longer than 5 secs sleep period?

---

### Post by Slim Odds on 2011-02-03
It would be better to have your script check that the network is up instead of just putting a delay.

---

### Post by cyberjar09 on 2011-02-04
> **Slim Odds said:**
> It would be better to have your script check that the network is up instead of just putting a delay.

i dont know shell scripting ... any help on the code?

---

### Post by cyberjar09 on 2011-05-14
I have recently upgraded to 11.04 and am currently in the process of setting up my startup applications and indicators. 

I have 2 questions 

1. I have installed **my-weather-indicator** indicator applet and set it to autostart. The **Startup Applications** also shows that the applet is meant to run from location "**/usr/share/my-weather-applet/my-weather-applet.py**"  But when the computer reboots, the applet does not start! I tried adding my own startup script "**sh -c '/usr/share/my-weather-applet/my-weather-applet.py'**" but it still fails to start. 
Whats going on here?! is it not starting because it is a python program? It runs fine when i run it from the launcher.It also runs fine from the terminal but when I close the terminal, the applet exits too. 

2. I also would like to startup certain applications in certain workspaces. Is it possible? if so, what do i have to add to the startup script to make it work? Example: If i want chrome to start in the 2nd workspace after a dealy of 5 seconds, what would I need to add to this script in the **Startup Applications** "**sh -c 'sleep 5 && /usr/bin/google-chrome'**". 

Thanks again for all your help. 
Much appreciated.

---

### Post by cyberjar09 on 2011-07-26
any idea where the install path for chromium browser (available for install from the Ubuntu Software Centre) is?

---

