---
title: "How to re-install the Japanese package."
date: 2010-07-29
forum: General Help
---

### Post by iguanaboy on 2010-07-29
Hello, I can't use Anthy to write in Japanese after some updates/upgrades to my Ubuntu 10.04, how can I re-install the Japanese language package? Thanks!

---

### Post by jsyl on 2010-07-30
First, make sure if you have the package or not.
Go to Terminal
```
anthy
```
_If nothing comes up:_
```
sudo aptitude install anthy
```

_If it's there but does not work:_
```
sudo aptitude purge anthy
```
Then
```
sudo aptitude install anthy
```

Hope this helps.

---

### Post by iguanaboy on 2010-07-30
Thanks, I did what you said, and nothing came up; did the upgrades erase my Anthy? Anyway, I re-installed it... and nothing changed. It still gives me the option to use Anthy, but nothing happens when I do (i.e. I can only type in Roman letters). What should I do?

---

### Post by drpjkurian on 2010-07-30
Hi
See whether you have the necessary packages of Japanese langugaes. Please check through synaptic package manager.

---

### Post by iguanaboy on 2010-07-30
Hmmm I looked at tha package manager, but I have no idea which ones I should install. There are hundreds... How can I find which ones I had in the first place, that allowed me to use Japanese?

---

### Post by drpjkurian on 2010-07-30
Hi
You can see my [blog]("http://ubuntucrack.blogspot.com/2010/07/hi-in-this-post-you-will-come-to-know.html") in which I have given instructions to type one native language of South India in Ubuntu known as Malayalam. You can try these instructions for Japanese too. (It worked for hebrew)

---

### Post by iguanaboy on 2010-07-30
I have tried what you said, and it is buggy as hell. I end up only being able to use SCIM on gedit (not on Internet websites for instance), and even there it doesn't work. SCIM gives me the choice of 3 input methods, but 2 of them are some kind of code and can't be used as such, and the 3rd is... Anthy, which not only doesn't work but instantly freezes gedit. Any ideas?

---

### Post by jsyl on 2010-07-30
Maybe now that you have anthy installed, you should run
```
sudo aptitude purge anthy
```
and then reinstall it.
When it uses purge, it removes all of the settings so that you can start from scratch at the reinstallation

---

### Post by iguanaboy on 2010-07-31
I did that - and it installed anthy m17n, which is not the one I used before ( I had simply "Anthy" with a gold symbol) and which doesn't work either. What confuses me also is that IBus used to always give me the choice between English and Japanese, now it's just anthy or "turn off input system". This gives me the impression that something has changed in-depth... but for the worse. Any radical ideas at this point?

---

### Post by drpjkurian on 2010-08-01
> I have tried what you said, and it is buggy as hell. 

Sorry mate

---

### Post by fuzetsu490 on 2010-08-01
hm, well its working for me, all i did was go to language support install all the options for Japanese, switched my input method system to ibus, went to ibus preferences and added anthy (m17n) as an input method. It works perfectly.

&#12354;&#12356;&#12358;&#12360;&#12362;

---

### Post by iguanaboy on 2010-08-02
All right, still fighting; I de-installed then re-installed the Japanese language package again, and now I have the original Anthy (with the golden crown) again! The problem is , neither Anthy nor anthy m17n work. I get this message when I open the IBus though, can someone explain it to me?

IBus has been started! If you cannot use IBus, please add the following lines in $HOME/.bashrc, and log in to your desktop again.
  export GTK_IM_MODULE=ibus
  export XMODIFIERS=@im=ibus
  export QT_IM_MODULE=ibus

Thanks, and sorry for the trouble.

---

### Post by fuzetsu490 on 2010-08-02
Have you selected Ibus as the keyboard input method system under 
system menu>administration>language support? Also did you install at least Japanese input under language support? I searched around a little and it seems like this was something that was happening to a lot of people with Ubuntu 9.10 here is a thread about it [http://ubuntuforums.org/showthread.php?t=1260793]("http://ubuntuforums.org/showthread.php?t=1260793")

---

### Post by iguanaboy on 2010-08-04
Yes, I did all that, and nothing works. I can turn Linux itself to Japanese easily, but nothing comes out of trying to write in Japanese. I'm now considering completely re-installing Ubuntu... sigh

---

