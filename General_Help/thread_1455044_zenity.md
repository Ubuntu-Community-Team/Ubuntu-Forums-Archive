---
title: "zenity"
date: 2010-04-15
forum: General Help
---

### Post by Mr Nemo on 2010-04-15
I've checked the man pages and tried google, but I still can't figure this out. Basically I'm trying to write a simple script that will have zenity display a yes or no question and then run a program depending on what I select. I'm also trying to figure out how to have zenity display a message after I select yes or no on the first display. I feel as though I'm forgetting to do something basic with the script...

---

### Post by kaibob on 2010-04-15
Have a look at this page, which has a lot of real-world examples:

[http://library.gnome.org/users/zenity/2.24/zenity.html](http://library.gnome.org/users/zenity/2.24/zenity.html)

If you post your actual script, we'll be happy to help. Zenity is quite easy to use once you get the hang of things.

---

### Post by Mr Nemo on 2010-04-15
alright here are the two

This one was just practice, its a jumbled mess since I've been screwing with it.

```

#!/bin/bash
zenity --question --title=Computer Scan --ok-label="Yes" --cancel-label="No" --text="<b>A Scan Of Your Computer Is Required!</b>\n\nWould you like to perform this scan now?"

if
if [ $? == 1 ]; then


zenity --info --text="Good"

exit 1


zenity --error --text="You pressed NO!"

```

and this is one is still practice but serves a purpose to me

```

#!/bin/bash
zenity --question --label="This will install software. Would you like to proceed?"
sudo apt-get -y install deluge
sudo apt-get -y install devede
sudo apt-get -y install vlc
sudo apt-get -y install chmsee
sudo apt-get -y install pidgin
sudo apt-get -y install screem
sudo apt-get -y install conky
sudo apt-get -y purge evolution
sudo add-apt-repository ppa:elementaryart/ppa
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo wget [http://newyork1.frostwire.com/frostwire/4.20.3/frostwire-4.20.3.i586.deb](http://newyork1.frostwire.com/frostwire/4.20.3/frostwire-4.20.3.i586.deb)
cd ~/ && sudo dpkg -i frostwire-4.20.3.i586.deb
sudo wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)
cd ~/
sudo tar -zxvf libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so ~/.mozilla/plugins/
read

```
For the second one I would like it to ask me the question and then run the program if I hit yes and cancel if I hit no.

Thanks for your help in advance.

---

### Post by kaibob on 2010-04-15
I rewrote your first script, as the second one has the same format. Your script includes stuff I don't believe is supported by zenity, and I have omitted that. I checked and the following does work. 

```
#!/bin/bash

zenity --question --title="Computer Scan" \
   --text="A Scan Of Your Computer Is Required! \
   Would you like to perform this scan now?"

if [[ $? -eq 0 ]] ; then
   zenity --info --text="Good"
else
   zenity --error --text="You pressed NO!"
fi
```

---

### Post by Mr Nemo on 2010-04-15
Thanks. It works better than mine, but I get the "You pressed NO" error message no matter what option I choose.

---

### Post by kaibob on 2010-04-15
> **Mr Nemo said:**
> Thanks. It works better than mine, but I get the "You pressed NO" error message no matter what option I choose.
I just tried the script again (copy and paste), and it worked fine. Did you copy and paste the whole thing? You have to use bash not sh in the first line. When run in a terminal window, do you get any error messages? Otherwise I don't know what's wrong. Perhaps another forum member will be able to help.

---

### Post by Mr Nemo on 2010-04-15
Your help and a couple of error notes from the terminal lead me to this:

```

#!/bin/bash

zenity --question --title="Computer Scan" \
   --text="A Scan Of Your Computer Is Required! \
   Would you like to perform this scan now?"

if [ $? -eq 0 ] ; then 
   zenity --info --text="Good"
else
   zenity --error --text="You pressed NO\!"
fi

```This seems to work. The double [ ] (brackets) seemed to be confusing ubuntu.

** I just saw your post, i dunno whats going on for I am just a beginner. I'm pretty sure I got your whole script.

** Your script is perfect, I found the problem on my end.

---

### Post by kaibob on 2010-04-15
> **Mr Nemo said:**
> ** Your script is perfect, I found the problem on my end.

I'm glad you got things working.

---

