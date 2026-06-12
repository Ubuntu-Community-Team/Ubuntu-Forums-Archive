---
title: "how do I step by step empty trash?"
date: 2012-03-19
forum: General Help
---

### Post by chenresig on 2012-03-19
OMG. I've been trying to delete trash can for two hours. I"ve been to google, youtube and ehow. Nothing works. The directions people leave are not clear enough. They just say enter this stuff in terminal and it will magically delete trash, but alas my trash can is plump with files that just won't go away. 

I have unbuntu 1.1 I believe. Can anyone easily and step by clear step, leaving nothing out, tell me exactly how to empty trash and now and in the future. 

And shout out to Ubuntu: Why did you make it so darn hard to empty trash. I love Ubuntu except for this juggernaut! Thanks so much, 

Alan

---

### Post by TeoBigusGeekus on 2012-03-19
Are these files deleted from an external storage device?

---

### Post by chenresig on 2012-03-19
Most were pix taken on a camera, then a tiny camera disk, then put on desktop and trransferred to folders. Now I put the folders in the trash and can't delete. Thanks so much for any help you can offer!

---

### Post by TeoBigusGeekus on 2012-03-19
Ok, probably a permissions' error.
Try this in a terminal
```
sudo rm -rf ~/.local/share/Trash/*
```

---

### Post by chenresig on 2012-03-19
Thanks, but of course, it didn't work. 

What about the spacing in the line you gave me? I assume it has to be exact like it looks? 

Also, Do I hit return after I type this in? No one has mentioned that. Or do I press nothing/or something else?

Thanks again so much!

---

### Post by chenresig on 2012-03-19
oh, it said 'command not found'

---

### Post by TeoBigusGeekus on 2012-03-19
Can't be.
Please copy and paste it in your terminal, hit enter, type your password and hit enter again (the password won't be seen as you type it).

---

### Post by chenresig on 2012-03-19
Darn, I appreciate your help sooo much, but it still isn't working. 

Maybe I'm getting my password wrong. Is it the same password I use when accept Ubuntu Updates? 

What about the spacing in the command line? DOes it have to be exact? 

If not, how do I retrieve any other password? 

I'm certain I have the Ubuntu Update passsword correct, 

Thanks again, 

Alan

---

### Post by TeoBigusGeekus on 2012-03-19
The spacing has to be exact. Just copy and paste it from my post.
Can you post the output from your terminal after you've issued the command?

EDIT: Yes, that's the password you must use.

---

### Post by chenresig on 2012-03-19
Oh, also, when i open Terminal there is already some words there followed by :~$

Is that supposed to be there?

So I enter the command line right after that, correct?

---

### Post by TeoBigusGeekus on 2012-03-19
> **chenresig said:**
> Oh, also, when i open Terminal there is already some words there followed by :~$

Is that supposed to be there?

So I enter the command line right after that, correct?

Yup.

---

### Post by chenresig on 2012-03-19
Thanks,

is there a space after the / and before the period? 

or is the /. have no spaces?

I can't believe this is so hard!

---

### Post by TeoBigusGeekus on 2012-03-19
> **chenresig said:**
> Thanks,

is there a space after the / and before the period? 

or is the /. have no spaces?

I can't believe this is so hard!

Just copy and paste it man.

---

### Post by chenresig on 2012-03-19
It won't copy and paste from your thread. So I copied and pasted in a word file then tried to paste it into the terminal and it won't paste either way. That why I asked about the period spacing. 

Sorry this is so annoying, I really appreciate your assistance!

---

### Post by TeoBigusGeekus on 2012-03-19
Ah, I see:
```
sudo_rm_-rf_~/.local/share/Trash/*
```
Replace all underscores (_) with a space.

EDIT: To paste into your terminal, select some text and middle click in the terminal.

---

### Post by HiImTye on 2012-03-19
highlight it and then middle click into the terminal window, this will paste it into it

---

### Post by ajgreeny on 2012-03-19
Highlight the command right click and copy, then go to the terminal, right click and paste.  it's as simple as that.  Context menus can be so useful! 

To use the keyboard it needs Ctrl+Shift+V to paste into terminal.

No, I never understood why either.  Why couldn't it be Ctrl+V as everywhere else?  I'm sure there must be a good reason for the difference, but I don't know it.

---

### Post by chenresig on 2012-03-19
check this out. It stilll didn't work, but I just opened the Trash, dragged and clicked them all in one big swoop and somehow a menu came up asking me to delete it all, which I did. 

I don't know how the heck  I did it, fyi.

EUREKA!  After 2 hours and 45 minutes, the Trash is empty! 

i even just created a fake folder and put it in trash and I can't duplicate what I did. 

What do you think happened?

Again, many mahalos from the island of Maui for your determined help! 

Aloha, 

Alan

---

### Post by HiImTye on 2012-03-19
> **ajgreeny said:**
> No, I never understood why either.  Why couldn't it be Ctrl+V as everywhere else?  I'm sure there must be a good reason for the difference, but I don't know it.
likely compatability with ncurses/other terminal programs that need ^V

---

### Post by TeoBigusGeekus on 2012-03-19
> **chenresig said:**
> check this out. It stilll didn't work...

Any error messages from the terminal?

---

### Post by chenresig on 2012-03-19
No error messages, but that -V thing did come up once or twice, but not consistently. 

One thing that could explain it: When I loaded Ubuntu on to this Dell laptop, from a cd, I wondered beforehand if the CD drive was damaged, cuz it made funny sounds while loading. However, ubuntu has always worked wiell , but when booting up it always says, error, no disk space available, but then it loads and everything works fine. 

Still trying to empty fake folders from trash but no luck. 

I wonder if the latest ubuntu version is any better.

---

### Post by TeoBigusGeekus on 2012-03-19
> **chenresig said:**
> No error messages, but that -V thing did come up once or twice, but not consistently. 

One thing that could explain it: When I loaded Ubuntu on to this Dell laptop, from a cd, I wondered beforehand if the CD drive was damaged, cuz it made funny sounds while loading. However, ubuntu has always worked wiell , but when booting up it always says, error, no disk space available, but then it loads and everything works fine. 

Still trying to empty fake folders from trash but no luck. 

I wonder if the latest ubuntu version is any better.

What -V thing?

Can you post a screenshot of your terminal after you've issued the command?

Also (about the running out of space message), can you post the output of
```
df -hT
```
?

---

### Post by chenresig on 2012-03-19
thanks Green! I didn't know I had to push ctrl/shift and v, I was just using ctrl paste! Now it does paste, but still won't delete my the new fake trassh folder I just created.

---

### Post by chenresig on 2012-03-19
sriyukteswar@sriyukteswar:~$ Sudo rm -rf ~/.local/share/Trash/*
No command 'Sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'udo' from package 'udo' (universe)
Sudo: command not found
sriyukteswar@sriyukteswar:~$ ^C
sriyukteswar@sriyukteswar:~$ 



I don't have a middle click?

---

### Post by HiImTye on 2012-03-19
don't use a capital S in sudo

---

### Post by TeoBigusGeekus on 2012-03-19
It's
```
sudo
```
not 
```
Sudo
```
Everything in Linux is case sensitive.

---

### Post by chenresig on 2012-03-19
thaniks teo, I did catch the case- sensitive  issue before; just typed it wrong in the example I pasted.

---

### Post by TeoBigusGeekus on 2012-03-19
Can you post the terminal's output using the correct command this time?

---

### Post by chenresig on 2012-03-19
yes, teo, here is what it said with line with a lower case T for trash vs upper case T for Trash. 

lower case t:

sriyukteswar@sriyukteswar:~$ sudo rm -rf ~/.local/share/trash/*
[sudo] password for sriyukteswar: 
sriyukteswar@sriyukteswar:~$ ^C
sriyukteswar@sriyukteswar:~$ ^C
sriyukteswar@sriyukteswar:~$ 

upper case T:

sriyukteswar@sriyukteswar:~$ sudo rm -rf~/.local/share/Trash/*
[sudo] password for sriyukteswar: 
rm: invalid option -- '~'
Try `rm --help' for more information.
sriyukteswar@sriyukteswar:~$

---

### Post by wojox on 2012-03-19
```
sudo rm -rf ~/.local/share/Trash/*
```

Neede a space between the f and tilde (~). Beat you Teo. :p

---

### Post by chenresig on 2012-03-19
how I miss old windows and Mac when you can just click so easily and the trash is gone!

---

### Post by TeoBigusGeekus on 2012-03-19
> **chenresig said:**
> yes, teo, here is what it said with line with a lower case T for trash vs upper case T for Trash. 

lower case t:

sriyukteswar@sriyukteswar:~$ sudo rm -rf ~/.local/share/trash/*
[sudo] password for sriyukteswar: 
sriyukteswar@sriyukteswar:~$ ^C
sriyukteswar@sriyukteswar:~$ ^C
sriyukteswar@sriyukteswar:~$ 

upper case T:

sriyukteswar@sriyukteswar:~$ sudo rm -rf~/.local/share/Trash/*
[sudo] password for sriyukteswar: 
rm: invalid option -- '~'
Try `rm --help' for more information.
sriyukteswar@sriyukteswar:~$

Do what wojox (hi mate!!!) posted and post back.

---

### Post by chenresig on 2012-03-19
All these great minds helping! Still with all correct spacing, my newly-created fake trash won't go away, even though the important trash went away accidentally (and luckily) when I selected all by dragging and clicking, then somehow, and it hasn't happened since, a menu popped up that let me empty trash....usually the 'empty trash' is not selectable. !

---

### Post by TeoBigusGeekus on 2012-03-19
Command and error message please.

---

### Post by chenresig on 2012-03-19
thanks for everyone's help. Must go to work now. 

Something must be amiss. 

NOthing worked like suggested. 

hmmmm? 

The only thing that work wasn't supposed to and I can't reduplicate it. 

Alan

---

### Post by TeoBigusGeekus on 2012-03-19
Reread the thread once you relax a bit.

---

### Post by JKyleOKC on 2012-03-19
> **ajgreeny said:**
> No, I never understood why either.  Why couldn't it be Ctrl+V as everywhere else?  I'm sure there must be a good reason for the difference, but I don't know it.I think the reason has to do with the convention that Ctrl+C is copy everywhere that uses Ctrl+V for paste, but in the CLI the Ctrl+C combination is used to interrupt a running process. I just assumed that, for consistency, developers added the shift requirement in the terminal emulators to all three hotkeys: cut, copy, and paste.

In any event, the context menus make it much simpler to use, since I use the mouse to select the material to be copied and don't need to switch to the keyboard to handle the transfer!

---

### Post by Derek Karpinski on 2012-03-19
> **teobigusgeekus said:**
> reread the thread once you relax a bit.
 
+1!

---

### Post by ajgreeny on 2012-03-20
> **JKyleOKC said:**
> I think the reason has to do with the convention that Ctrl+C is copy everywhere that uses Ctrl+V for paste, but in the CLI the Ctrl+C combination is used to interrupt a running process. I just assumed that, for consistency, developers added the shift requirement in the terminal emulators to all three hotkeys: cut, copy, and paste.

In any event, the context menus make it much simpler to use, since I use the mouse to select the material to be copied and don't need to switch to the keyboard to handle the transfer!
Oh crikey!  Thanks for that thought JK, it makes sense when you think about it, which I obviously hadn't, or not sufficiently.  I was just considering paste, not the two, copy/paste together.

---

