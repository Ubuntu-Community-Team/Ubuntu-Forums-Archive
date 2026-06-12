---
title: "Rhythmbox terminal commands"
date: 2010-08-26
forum: General Help
---

### Post by BrockStrongo on 2010-08-26
Does anyone know the command line option to show rhythmbox?   

Basically I just want to make a shortcut to show the rhythmbox screen as opposed to clicking the icon and selecting show rhythmbox

rhythmbox-client --(option) --no-start

Thanks

---

### Post by darolu on 2010-08-26
You can see the manual with:
```
man rhythmbox
```
You will notice that there is no option to do what you want, I also find this new behaviour very annoying so what I did, is go to the add-ons (plugins) options (under Edit) and disable the tray icon.

---

### Post by BrockStrongo on 2010-08-26
Thanks. 
     I was hoping someone knows of a way to accomplish this, I like the behavior of rhythmbox with the notification icon on (close window, song keeps playing) so I would like to keep the icon enabled.
   There's got to be a command for this right? 
Any thoughts,

---

### Post by M4he on 2010-08-26
I've read through your posts multiple times but I still don't entirely get what you want to do. Could you please explain it a bit more detailed?

Do you want to start rhythmbox (making the icon appear on the panel) **and** open up the interface at once?

Just type
```
rhythmbox & rhythmbox
```in the terminal.

---

### Post by BrockStrongo on 2010-08-26
I want to have a button or keystroke that will show the rhythmbox screen.  

Right now I have to click on the icon in the systray and select "Show Rhythmbox" I think it would be much more convenient to hit ctrl+r or something like that to "unhide" the rhythmbox interface.

I hope this makes a little more sense, I don't know why I'm having such a hard time articulating my goal, not enough coffee I guess

---

### Post by M4he on 2010-08-26
[LIST]
[*]Go to System -> Preferences -> Keyboard Shortcuts and click "Add"
[*]As name type something you like, as command type "rhythmbox" and hit "Apply"
[*]Then click on the right side of the new command where you can set the key combination and press Ctrl + R (or whatever shortcut suits you)
[/LIST]

---

### Post by BrockStrongo on 2010-08-26
Thanks for the reply, 
    I think I'm not being clear enough with what I am after, I apologize for that. 
   I know how to make keyboard shortcuts, what I am missing is the command I need to assign to the shortcut.
eg:  "rhythmbox-client --next --no-start" advances rhythmbox to the next track. I could create a keyboard shortcut (alt+1) to initiate this command.  
      "rhythmbox-client --hide --no-start" hides the user interface while still allowing music to continue playing.

What I am after is the command that would unhide the user interface, there appears to be none in the rhythmbox man pages, but there has to be some command to accomplish this.

I appreciate all the help, I've got this idea of what I want to do, and really appreciate your input, and ideas.
Thanks

---

### Post by M4he on 2010-08-26
But the command "rhythmbox" should unhide it. It does at least for me...

Oddly enough "rhythmbox-client --hide --no-start" isn't working for me while any other command with rhythmbox-client does. I'm hiding the UI simply by closing the Rhythmbox window.
(The icon in the panel remains and it keeps playing)

So maybe the way of "hiding" Rhythmbox between our methods is different and therefore the solution is too...

---

### Post by BrockStrongo on 2010-08-26
Thats it! you've done it! :) The simplest answer is usually the right one.
Here I am looking for a command to show the rhythmbox ui and it is simply "rhythmbox" like you said in your previous post. Sorry I guess I can't read either. 
This is where I was getting the client commands [http://www.glump.net/howto/rhythmbox_global_shortcuts](http://www.glump.net/howto/rhythmbox_global_shortcuts)
Thanks for putting up with my not reading the post properly

---

### Post by M4he on 2010-08-26
I'm glad I could be of help :)

---

### Post by andypi on 2010-10-01
> **M4he said:**
> Oddly enough "rhythmbox-client --hide --no-start" isn't working for me while any other command with rhythmbox-client does.

This is the problem I'm having, anyone managed to solve it?

---

### Post by RgnKjnVA on 2010-12-28
> **M4he said:**
> But the command "rhythmbox" should unhide it. It does at least for me...

Oddly enough "rhythmbox-client --hide --no-start" isn't working for me while any other command with rhythmbox-client does. I'm hiding the UI simply by closing the Rhythmbox window.
(The icon in the panel remains and it keeps playing)

So maybe the way of "hiding" Rhythmbox between our methods is different and therefore the solution is too...

+1 re: --hide not working. It used to until very recently. I've had key shortcuts configured for rhythmbox for years. Frankly, I wish --hide could be replaced with a --toggleui switch but we're stuck with two different commands to hide/display the UI. I'm off to see if there is a bug against this --hide issue.

---

