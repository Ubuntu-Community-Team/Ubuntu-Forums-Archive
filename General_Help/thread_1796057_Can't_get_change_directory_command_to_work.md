---
title: "Can't get change directory command to work"
date: 2011-07-03
forum: General Help
---

### Post by User1138 on 2011-07-03
Basically, I'm in the terminal and I type in:

cd desktop (or downloads or whatever)

and nothing happens. I'm probably just being legendarily thick, but where am I going wrong?

---

### Post by bowens44 on 2011-07-03
When you say nothing happens, what exactly do you mean?

Does it come back and tell you no such directory? Does it give an error?

Keep in mind that everything is case sensitive.

If you are in your home directory you would do 'cd Downloads' (without the quotes) to change to that directory

---

### Post by sammiev on 2011-07-03
> **User1138 said:**
> Basically, I'm in the terminal and I type in:

cd desktop (or downloads or whatever)

and nothing happens. I'm probably just being legendarily thick, but where am I going wrong?

For downloads I use "cd Downloads" It is also case sensitive. GL :)

---

### Post by User1138 on 2011-07-03
It comes back with "no such file or directory". I've taken care to make sure what I type is case sensitive. Any thoughts?

---

### Post by nothingspecial on 2011-07-03
Either there is no Downloads directory in the directory you are issuing the command from, or you a typing it wrong.

You sure you are using a big D

[COLOR="Red"][SIZE="2"]D[/SIZE][/COLOR]ownloads not [COLOR="Red"][SIZE="2"]d[/SIZE][/COLOR]ownloads

---

### Post by User1138 on 2011-07-03
> **nothingspecial said:**
> Either there is no Downloads directory in the directory you are issuing the command from, or you a typing it wrong.

You sure you are using a big D

[COLOR=Red][SIZE=2]D[/SIZE][/COLOR]ownloads not [COLOR=Red][SIZE=2]d[/SIZE][/COLOR]ownloads

Quite sure thankyou :P

Thanks guys, I'll keep on trying. 

I must be the biggest newb ever.

---

### Post by in-dust-rial on 2011-07-03
hey there,
a more general remark:
first of all,
look up the difference between absolute and relative path!
( [http://www.geekinterview.com/question_details/3499](http://www.geekinterview.com/question_details/3499) )

then use 
[HTML]$pwd[/HTML]
should display where you are in terms of an ABSOLUTE path.
[HTML]$ls[/HTML]
should then show what is within this path.

when you now use the "cd" command without an REALATIVE PATH you should use a folder which was listed by the "ls" command.


I still work like this on unknown systems or if things get tricky. 
the "pwd" command is your friend.

second remark:
use completion of the console(terminal) if it is enabled. if completion is enabled depends on the kind of shell (console-software) which is used.

[HTML]$ls [TAB][/HTML]
where [TAB] indecates to press the tabulator key on your keyboard.
(NOTE: there is a space between the "ls" and the "tab")

now the terminal should show different available options to you. 


see below for video demos:
[http://www.google.com/search?client=ubuntu&channel=fs&q=terminal+completion&ie=utf-8&oe=utf-8#sclient=psy&hl=en&safe=off&client=ubuntu&hs=FH6&channel=fs&tbm=vid&source=hp&q=bash+completion&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=deb24ccd75812d3e&biw=1010&bih=779](http://www.google.com/search?client=ubuntu&channel=fs&q=terminal+completion&ie=utf-8&oe=utf-8#sclient=psy&hl=en&safe=off&client=ubuntu&hs=FH6&channel=fs&tbm=vid&source=hp&q=bash+completion&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=deb24ccd75812d3e&biw=1010&bih=779)


good luck

---

### Post by oldos2er on 2011-07-03
> **User1138 said:**
> Basically, I'm in the terminal and I type in:

cd desktop (or downloads or whatever)

and nothing happens. 

Can you copy and paste your commands and terminal output here?

---

### Post by bowens44 on 2011-07-03
Try this:

cd ~/Downloads

---

### Post by mike555 on 2011-07-03
To make things easier in the future you might want to install "nautilus-open-terminal" , that will let you open terminal in any folder.......

---

### Post by barkhat on 2011-08-14
After searching around and trying find the answer on my own, I am seeking advice.  

I want to cd into my Ubuntu One folder (from my home folder).  I can't find anything that tells me what to do when you have a multi-word directory name.
I've tried cd Ubuntu One, cd Ubuntu_One, cd Ubuntu-One. I would like to learn to do this through the terminal to be quick, but don't know how. 

Please help!

Thank you.:popcorn:

---

### Post by WyleECoyote on 2011-08-14
> **barkhat said:**
> After searching around and trying find the answer on my own, I am seeking advice.  

I want to cd into my Ubuntu One folder (from my home folder).  I can't find anything that tells me what to do when you have a multi-word directory name.
I've tried cd Ubuntu One, cd Ubuntu_One, cd Ubuntu-One. I would like to learn to do this through the terminal to be quick, but don't know how. 

Please help!

Thank you.:popcorn:

you have a few options, you can either $ cd "Ubuntu One" or you can $ cd Ubuntu\ One

---

### Post by spiky001 on 2011-08-14
Try ```
cd "Ubuntu One"
```

---

### Post by barkhat on 2011-08-14
> **WyleECoyote said:**
> you have a few options, you can either $ cd "Ubuntu One" or you can $ cd Ubuntu\ One

Wow, thank you very much! I have not heard of either of these ways before and I couldn't figure out how to phrase it correctly when I was searching.

That did it!

---

### Post by barkhat on 2011-08-14
> **spiky001 said:**
> Try ```
cd "Ubuntu One"
```

Thank you very much, Spiky001 for your quick response. All set now.

---

### Post by JKyleOKC on 2011-08-14
Just a note to explain to you what is happening:

The command interpreter uses the space character as the dividing line between parameters being passed to the command. Thus the command "cd Ubuntu One" (with no quotes) tells it to change to the directory "Ubuntu" and to treat "One" as an additional parameter.

To force a phrase that includes spaces to be treated as a single parameter, you can surround the entire phrase with double quotes. Alternatively, you can "escape" the space character with the backslash character, which causes the interpreter to treat it as just a space, not a divider. Either way you do it gives the same result.

Quite a few more characters have special meaning to the command interpreters, and different shell programs have different lists of them. Ubuntu uses "bash" as its shell, so you can search for that program name to find tutorials about it. Entire books have been written about its use, so don't expect to learn all about it in a single message thread...

---

### Post by barkhat on 2011-08-14
> **JKyleOKC said:**
> Just a note to explain to you what is happening:

The command interpreter uses the space character as the dividing line between parameters being passed to the command. Thus the command "cd Ubuntu One" (with no quotes) tells it to change to the directory "Ubuntu" and to treat "One" as an additional parameter.

To force a phrase that includes spaces to be treated as a single parameter, you can surround the entire phrase with double quotes. Alternatively, you can "escape" the space character with the backslash character, which causes the interpreter to treat it as just a space, not a divider. Either way you do it gives the same result.

Quite a few more characters have special meaning to the command interpreters, and different shell programs have different lists of them. Ubuntu uses "bash" as its shell, so you can search for that program name to find tutorials about it. Entire books have been written about its use, so don't expect to learn all about it in a single message thread...

Thank you so much, Jim. I really appreciate that information!:D

---

### Post by JKyleOKC on 2011-08-14
You're quite welcome!

---

