---
title: "Terminal commands"
date: 2011-02-10
forum: General Help
---

### Post by wrighty.uk.gorl on 2011-02-10
Hi Every one first off all thanks to any one who will help me, And would like to also add that i only started using ubuntu about 2 weeks ago been a windows user all my life.

now the question and the problem i am having !

I started using computer when it was all dos driven so thought i was going to be fine using the terminal in ubuntu the problem i am facing is i can not quite get my head round why is it if i load the terminal. and the first this i type is dir or ls it gives me a list off directories. So why is it if i type cd /pictures i get no such file or directory ? Confused

This also bugging the jebus out off me is i am trying to get into my usb pen drive from the terminal to run a program i have on there. 

so i type cd /media
then typed ls 
is displayed New Volume <-- This being the name off my pen drive
i have tried every this to get into there but the commands i would use in dos are not playing ball.

Can some one please explain how to get into my usb pen then tell me were i can go read on this as i really can not get my head around this at moment.

---

### Post by howefield on 2011-02-10
> **wrighty.uk.gorl said:**
> So why is it if i type cd /pictures i get no such file or directory ?

Linux is case sensitive, you probably need cd /Pictures

> so i type cd /media
then typed ls 
is displayed New Volume <-- This being the name off my pen drive
i have tried every this to get into there but the commands i would use in dos are not playing ball.

A tip is to use the tab key to auto complete as you will need to escape the space between New and Volume.

cd Ne and hit the tab key.

It should come out as cd New\ Volume

---

### Post by uRock on 2011-02-10
For your pictures folder you will want to use a capital P in the command. The terminal is case sensitive. You will also need to put the ~ into the command to tell the system you are looking in your Home folder like this, ```
cd ~/Pictures
```

Not sure about mounting your thumb drive but if it is named New Volume, the you would need to type it with a back slash like this, ```
New\ Volume
```

---

### Post by AlphaLexman on 2011-02-10
you need to remove the '/' in front of the foldername and after the command 'cd'

---

### Post by oldos2er on 2011-02-10
Bash commands are for the most part different than DOS commands, true. Linux is case-sensitive, so you'd need to type *cd Pictures*, for example. Your command *cd /pictures* tells the shell to search for a folder named 'pictures' from the root folder ( / = root folder) which won't exist by default.

Also the shell doesn't deal with spaces in file or folder names very well, so there are a couple different things you can do; one, put quotation marks around the name, e.g. *cd "New Volume"* or use the escape character \ to tell bash to ignore the spaces, *cd New\ Volume*. Or use Tab completion and let bash do the work for you, cd New<Tab>

More info: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by wrighty.uk.gorl on 2011-02-10
You all are stars a few days this have been eating away at me and now it makes sence. Got in there right aways 

Thank you all so much

---

