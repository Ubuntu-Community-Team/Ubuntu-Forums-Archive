---
title: "add new keyboard key combination"
date: 2011-03-18
forum: General Help
---

### Post by baumtopf on 2011-03-18
Hello Ubuntu users,

I would like do add a new keyboard key combination for a function like Alt + F4.
for example shift + control + s.
Up to now, i was successful with exchanging the function Alt + F4.
But I don't like to exchange, because I need Alt + f4 and shift + control + s for the function close window at the same time.

So how can I add a new keyboard combination without to exchange?

Regards, Juergen

---

### Post by garvinrick4 on 2011-03-18
Keyboard shortcuts:
To change or add a new one.

---

### Post by baumtopf on 2011-03-18
Hello garvinrick4,

thanks for answer!

I visited your link and there are a lot of topics.
Do you mean this [2.8.4 Add repository keys]("http://ubuntuguide.org/wiki/Ubuntu:Maverick#Add_repository_keys")
topic?

Regards, Juergen
[]("http://ubuntuguide.org/wiki/Ubuntu:Maverick#Add_repository_keys")

---

### Post by grahammechanical on 2011-03-18
I do not think that garvinrick4 means Add repository keys. Unless of course I am misunderstanding your question. I think that garvinrick4 is advising that you go to System>Preferences>Keyboard Shortcuts and do what you want in that utility.

Regards.

---

### Post by baumtopf on 2011-03-18
Hello grahammechanical,
thanks for answer

I follow your path:

System>Preferences>Keyboard Shortcuts

And I have tried to add a new shortcut in this utility.
But it doesn't function and I don't know why.
Please watch this YouTube Video. In this Video you can see how I tried to add a new shortcut:

Please watch this:

[http://www.youtube.com/watch?v=9_TgkUN5n94](http://www.youtube.com/watch?v=9_TgkUN5n94)

Regards, Juergen

---

### Post by baumtopf on 2011-03-19
Hello again!

I tried to add a new keyboard shortcut in "Keyboard Shortcuts" and in "CompizConfig Settings Manager". It doesn't work. 

Please watch these YouTube Clips. It shows you my problems:

[http://www.youtube.com/watch?v=_ZESczCUg8g](http://www.youtube.com/watch?v=_ZESczCUg8g)

[http://www.youtube.com/watch?v=NhKIC3RqSFs](http://www.youtube.com/watch?v=NhKIC3RqSFs)

Please help!

Regards, Juergen

---

### Post by Frogs Hair on 2011-03-19
If you using compiz with desktop effects enabled that will limit the use of some keyboard short cuts . Compiz (CCSM) uses many different key bindings .

[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

---

### Post by Krytarik on 2011-03-19
Hi Jürgen,

I just yet watched your videos. And I need to say, I didn't experience that kind of audio/visual presentation of an issue so far, great!! :D

I'm not sure, if you are running Compiz or not, meaning having desktop effects enabled
You may check in "System -> Preferences -> Appearance -> Visual Effects":
- "None" means Metacity
- anything else means Compiz

To enter a new keyboard shortcut for your desired action:

Metacity:
- go to "System -> Preferences -> Keyboard Shortcuts"
- click at the desired action
- you will notice that the field which stated the current shortcut now reads "New shortcut..." or in German "Neue Tastenkombination..."
- now you can simply press the desired keys to set the new keyboard shortcut

Compiz:
- "System -> Preferences -> CompizConfig Settings Manager -> General Options -> Key bindings"
- click at the field which states the current shortcut
- click at "Grab key combination" (I don't know the German name)
- now you can simply press the desired keys to set the new keyboard shortcut

Greetings.

---

### Post by stinkeye on 2011-03-19
> **baumtopf said:**
> Hello Ubuntu users,

I would like do add a new keyboard key combination for a function like Alt + F4.
for example shift + control + s.
Up to now, i was successful with exchanging the function Alt + F4.
But I don't like to exchange, because I need Alt + f4 and shift + control + s for the function close window at the same time.

**So how can I add a new keyboard combination without to exchange?**

Regards, Juergen

If you want to keep your original alt+F4 key combination for closing a window
and add another key also for the close window function...

Install wmctrl
```
sudo apt-get install wmctrl
```


Open keyboard shortcuts and hit the add button
```
Name: **close active window**
Command:  **wmctrl -c :ACTIVE:**
```
Click on the apply button.

Click on the right hand side of the **close active window** entry
and key in your shortcut.

---

### Post by Krytarik on 2011-03-19
Ok, stinkeye, you may be right. I got apparently somehow distracted from the OP by those videos, because they indicated a different intention to me.

The way described above by *stinkeye* regards Metacity, if you are using Compiz:
- go to "System -> Preferences -> CompizConfig Settings Manager -> Commands"
- add the command at the first tab, "Commands"
- assign a key combination to it at the "Key Bindings" tab

---

### Post by stinkeye on 2011-03-19
> **Krytarik said:**
> Ok, stinkeye, you may be right. I got apparently somehow distracted from the OP by those videos, because they indicated a different intention to me.

The way described above by *stinkeye* regards Metacity, if you are using Compiz:
- go to "System -> Preferences -> CompizConfig Settings Manager -> Commands"
- add the command at the first tab, "Commands"
- assign a key combination to it at the "Key Bindings" tab
I might be wrong too, sometimes it's a bit hard too understand when English
isn't the posters first language. :???:

---

### Post by Krytarik on 2011-03-19
> **stinkeye said:**
> I might be wrong too, sometimes it's a bit hard too understand when English
isn't the posters first language. :???:
LOL:D  I hope we will know it soon!

---

### Post by baumtopf on 2011-03-19
Hello stinkeye and Krytarik,

I have tried stinkeye's and Krytarik's idea. But it doesn't work.

To understand my problem, please watch these videos
Or you can visit my pictures in my attachment

Stinkeye's idea:
[http://www.youtube.com/watch?v=AjLtzamK1VU](http://www.youtube.com/watch?v=AjLtzamK1VU)
Result: function is disabled

Krytarik's idea:
[http://www.youtube.com/watch?v=19mjuT6oq7Q](http://www.youtube.com/watch?v=19mjuT6oq7Q)
Result: Error warning

I think that I insert the right shortcut in Metacity but combine with the wrong command.
So I need the right command.

Do you understand my English or is it too bad?

I would be glad if you improve my English.

Please give me Feedback!

Regards, Juergen

---

### Post by baumtopf on 2011-03-20
Hello ubuntuusers,

Don't you have any ideas, Krytarik and Stinkeye?

Or anybody else?

Regards, Juergen

---

### Post by Krytarik on 2011-03-20
First, when you simply *edit* a post, the subscribed members don't get notified!
Because of that I didn't notice until now.

Then, please clarify if you want to *add* an additional shortcut with the same function, like you wrote in the OP. Or if you simply want to *change* the key combination of an existing shortcut.

Also, which window manager do you run then, Metacity or Compiz?

---

### Post by Script Warlock on 2011-03-20
> **baumtopf said:**
> Hello stinkeye and Krytarik,

I have tried stinkeye's and Krytarik's idea. But it doesn't work.

To understand my problem, please watch these videos
Or you can visit my pictures in my attachment

Stinkeye's idea:
[http://www.youtube.com/watch?v=AjLtzamK1VU](http://www.youtube.com/watch?v=AjLtzamK1VU)
Result: function is disabled

Krytarik's idea:
[http://www.youtube.com/watch?v=19mjuT6oq7Q](http://www.youtube.com/watch?v=19mjuT6oq7Q)
Result: Error warning

I think that I insert the right shortcut in Metacity but combine with the wrong command.
So I need the right command.

Do you understand my English or is it too bad?

I would be glad if you improve my English.

Please give me Feedback!

Regards, Juergen

Stinkeye's idea is working...

just stick to
 
[COLOR="Blue"]wmctrl -c :ACTIVE:[/COLOR]

according to your video you saw "disabled" thats because you didn't click that thing and supply your desired keys. when clicking heres what it says "new shortcut" and thats the time you press the keys you want to use.

---

### Post by stinkeye on 2011-03-20
Yes as Script Warlock said once you have entered
```
Name: close active window
Command:  wmctrl -c :ACTIVE:
```
and clicked on the apply button
you click on "**disabled**" and "**New shortcut.**." will be displayed.
Now just enter the keys you want to use.
Don't type in c t r l ....
Just press the keys you want to use.

...and why did you decide you don't like -c and use -w instead. lol
**-c** closes the window specified.
**-w** will do nothing besides giving you the error "**Unknown workaround: :active:**"

---

### Post by baumtopf on 2011-03-21
Hello ubuntuusers,

now it works in Keyboard Shortcuts!

Where did you find the commands? for examlple wmctrl -c :ACTIVE
Do you know some other very useful commands for shortcuts?

thanks for help and critics!

Krytarik, do you mean, that I shoudn't mention you in my contributions, for example in the videos? If this is problem, I will delete immediatelythe the videos .

Please give a feedback!

Greetings, Jürgen

---

### Post by stinkeye on 2011-03-21
wmctrl is a command that can be used to interact with an X Window manager.
For more commands look at the manual for wmctrl.
Most applications will have a manual page.
eg to view the wmctrl manual page enter in the terminal
```
man wmctrl
```
To exit the man page press "q".

---

### Post by Krytarik on 2011-03-21
> **baumtopf said:**
> 
Krytarik, do you mean, that I shoudn't mention you in my contributions, for example in the videos? If this is problem, I will delete immediatelythe the videos .

Actually, I didn't watch your latest videos, because wanted to have answers to my questions first. But if you actually mentioned me in them, I'm absolutely fine with it, since it isn't my real name. ;-)   I somehow even appreciate it, thanks! :-)

Great that it finally works!

---

