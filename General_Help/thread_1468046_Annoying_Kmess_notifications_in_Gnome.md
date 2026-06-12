---
title: "Annoying Kmess notifications in Gnome"
date: 2010-05-01
forum: General Help
---

### Post by born_to_be_different on 2010-05-01
Hey everyone! :)

I've recently upgraded to 10.04 and I love it, however, I have found myself one problem which is quite annoying! :( I use Kmess as my IM client (I seem to prefer it for some reason!) and ever since I've upgraded, instead of the notifications displaying with Gnome's notification system, they've been appearing as a new window (see attachment.) This is much more annoying as I actually have to perform an action to get rid of it!

Basically, I would like to stop this and get them re-appearing with Gnome's notification system like before in 9.10! 

Thanks in advance! :)

Graham

---

### Post by vzhen on 2010-05-02
me 2.
let me know if u got the solutions

Thx

---

### Post by born_to_be_different on 2010-05-02
Sorry, I don't know anything yet! :(

If I do manage to find something out, then I'll message you! :)

---

### Post by born_to_be_different on 2010-05-03
***Bump-ty Bump, Bump***

Sorry, I don't like to bump threads but I would really like to get this  fixed. :(

Any ideas as well would be greatly appreciated! :)

---

### Post by xeemeex on 2010-05-03
This problem affects me too. Sometimes appears that same annoying window, sometimes another kind of undecorated window that is more similar to a notification and less annoying, but still ugly.

---

### Post by born_to_be_different on 2010-05-05
> **xeemeex said:**
> This problem affects me too. Sometimes appears that same annoying window, sometimes another kind of undecorated window that is more similar to a notification and less annoying, but still ugly.

What do you mean "another kind of undecorated window..."? :confused: 

Could you possibly post a screen-shot, please? :)

---

### Post by ntomka on 2010-06-07
1. Run ```
sudo aptitude install libnotify-bin
```

2. Actions menu » Kmess settings » Alerts

3. Choose the alert(s) you want to modify

4. Disable *"Show a message in a popup"*

5. Enable *"Run command"*. To the textbox after it enter this: ```
notify-send Kmess %25s
```

Detailed: the [FONT="Courier New"]notify-send[/FONT] command sends a message by the notify osd system. The first argument is the title, the second one is the message itself. %25s means the original Kmess message, the client will replace it.

Repeat it for all the message you want to control.
You can change the above command parameters.
I haven't found out yet how to show up the partner's avatar in the message, but [FONT="Courier New"]notify-send[/FONT] has a [FONT="Courier New"]-i[/FONT] command line switch, wich by it can show an icon for the message.

The bad thing about this, the notify osd system can't handle HTML tags, so if your partner has msn plus tagged nicknames, the codes will be shown in the message. You can have a workaround for it by adding your own alternate nickname for the partner or disable the plus coloring option for the partner list.

---

### Post by born_to_be_different on 2010-06-07
> **ntomka said:**
> 1. Run ```
sudo aptitude install libnotify-bin
```2. Actions menu » Kmess settings » Alerts

3. Choose the alert(s) you want to modify

4. Disable *"Show a message in a popup"*

5. Enable *"Run command"*. To the textbox after it enter this: ```
notify-send Kmess %25s
```Detailed: the [FONT=Courier New]notify-send[/FONT] command sends a message by the notify osd system. The first argument is the title, the second one is the message itself. %25s means the original Kmess message, the client will replace it.

Repeat it for all the message you want to control.
You can change the above command parameters.
I haven't found out yet how to show up the partner's avatar in the message, but [FONT=Courier New]notify-send[/FONT] has a [FONT=Courier New]-i[/FONT] command line switch, wich by it can show an icon for the message.

The bad thing about this, the notify osd system can't handle HTML tags, so if your partner has msn plus tagged nicknames, the codes will be shown in the message. You can have a workaround for it by adding your own alternate nickname for the partner or disable the plus coloring option for the partner list.

THANK YOU!! :D
This is a really good work around for the time being! :P

I would really like to get Knotify working at some point in time, but at the moment, this'll do me just dandy! :)

---

### Post by erjoalgo on 2010-07-19
same problem, workaround seems like a bitch. i will use pidgin and keep an eye on this thread

---

### Post by xtremox on 2010-10-07
> **ntomka said:**
> 1. Run ```
sudo aptitude install libnotify-bin
```

2. Actions menu » Kmess settings » Alerts

3. Choose the alert(s) you want to modify

4. Disable *"Show a message in a popup"*

5. Enable *"Run command"*. To the textbox after it enter this: ```
notify-send Kmess %25s
```

Detailed: the [FONT="Courier New"]notify-send[/FONT] command sends a message by the notify osd system. The first argument is the title, the second one is the message itself. %25s means the original Kmess message, the client will replace it.

Repeat it for all the message you want to control.
You can change the above command parameters.
I haven't found out yet how to show up the partner's avatar in the message, but [FONT="Courier New"]notify-send[/FONT] has a [FONT="Courier New"]-i[/FONT] command line switch, wich by it can show an icon for the message.

The bad thing about this, the notify osd system can't handle HTML tags, so if your partner has msn plus tagged nicknames, the codes will be shown in the message. You can have a workaround for it by adding your own alternate nickname for the partner or disable the plus coloring option for the partner list.

thanks is worked fine for me:guitar:

---

### Post by Elfy on 2012-05-18
Old thread closed.

Please start a new thread for your issue.

---

