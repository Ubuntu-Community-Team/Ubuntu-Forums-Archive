---
title: "How do I type Chinese (simplified cangjie) on Ubuntu?"
date: 2010-03-21
forum: General Help
---

### Post by superarthur on 2010-03-21
I checked Chinese in system>admin>language support. I installed SCIM.
However, I still can't find a way for me to switch the input method from English to Chinese.

It's the first time I am getting fed up with Ubuntu (wait.... maybe the second time). Everything in Ubuntu seems to be better than Windows to me. But how can it be so darn difficult to switch to another input language. It's just a few clicks for me in Windows. One of the main reason for people to use computer is word processing. It should be easy for someone to boot up Ubuntu and type a document in the language they preferred. (well, to be honest, I don't type Chinese that often, I just want it to be there in case I need it. But think about other people who have to type in their language, and become discouraged in using Ubuntu because so much work in needed to switch the input language)

Please help me :'(

---

### Post by Ampi on 2010-03-21
Here is my explanation on input methods, where you can choose Chinese simplified instead of Japanese...
I use to use SCIM but somehow it doesn't seem to work anymore. The Ubuntu 9.10 now has automatically IBUS installed so I use that program that does seem to work but it takes a minute.. :)


**Japanese (and other) input methods**
With Ubuntu 9.10 IBus comes installed. With this little program you can write in all kinds of different languages like Japanese and Russian.
You can find this program under System -> Preferences -> IBus Preferences. First you will be asked:

    IBus deamon is not started. Do you want to start it now?

Choose "Yes". Then you see the following message:

    IBus has been started! If you can not use IBus, please add below lines in $HOME/.bashrc, and relogin your desktop.
    export GTK_IM_MODULE=ibus
    export XMODIFIERS=@im=ibus
    export QT_IM_MODULE=ibus

Click "Ok" and go to the "Input Method" tab and click on "Select an input method". There you can choose any language you want. I, for example, chose Japanese - Anthy. Click "Add" and the input method will be added to the list.
Now if you actually want to write in another language, you can either left-click on the icon on the right in your panel or use the shortcut defined in IBus Preferences in the "General" tab..
Now start typing: &#26085;&#26412;&#35486;&#12289;&#12424;&#12363;&#12387;&#12383;&#12290;&#12290;&#65281;

If you want the IBus daemon to be automatically started when you reboot your computer, go to System -> Preferences -> Startup Applications. Click on "Add" and write down the following:

    Name: IBus daemon
    Command: /usr/bin/ibus-daemon -d
    Comment: Start IBus daemon when Gnome starts

Now the IBus daemon will start when Gnome starts.

---

### Post by superarthur on 2010-03-21
Thanks. It works.
It's a still a bit inconvenient...
When I have IBUS activated and type English, it highlights the word when I am typing, which seems a bit awkward.
Secondly, the Chinese input is a bit awkard as well. Normally, &#26408; is d[space]. Now I have to type dd instead. It's a pain when there is a small change in the way how it accepts my input (if you switch a and b on your keyboard, it would be really uncomfortable).
Thirdly, I still think this method is a bit user-unfriendly. Ubuntu emphasis ease of use. And no one has a clue what IBUS is and that it's related to changing the input method unless they read about it.

btw, how to change the topic to [SOLVED]?

---

### Post by Ampi on 2010-03-21
I think if you go to the very first post you can change the prefix to SOLVED. 

If you want to type English you should have IBUS off (CTRL+Space) because then you simply type in your current installation keyboard configuration. When you actually want to use IBUS then use it only for Chinese. I think if not you type English through IBUS and then it might be weird...

I believe SCIM is more user-friendly but somehow it didn't work that well either, so hence the change of software. I guess Ubuntu, in these times, hasn't accepted yet that one user can be a multi-language-user. So the choice of language input is only for the entire OS. There should be a better alternative. But we'll have to wait..!

---

### Post by superarthur on 2010-03-21
Thanks. I removed English from IBUS and use control+space to switch between English and Chinese.

---

### Post by leonbravo on 2010-05-01
> **Ampi said:**
> I think if you go to the very first post you can change the prefix to SOLVED. 

If you want to type English you should have IBUS off (CTRL+Space) because then you simply type in your current installation keyboard configuration. When you actually want to use IBUS then use it only for Chinese. I think if not you type English through IBUS and then it might be weird...

I believe SCIM is more user-friendly but somehow it didn't work that well either, so hence the change of software. I guess Ubuntu, in these times, hasn't accepted yet that one user can be a multi-language-user. So the choice of language input is only for the entire OS. There should be a better alternative. But we'll have to wait..!

arigato! wat kynd of thipos?

---

### Post by Ampi on 2010-05-02
Dozo! Well, not that kind!! I don't remember which ones, but I know they were from a 5-year-old-style ;)

---

