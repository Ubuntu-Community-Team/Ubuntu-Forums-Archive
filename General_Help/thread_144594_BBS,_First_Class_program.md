---
title: "BBS, First Class program?"
date: 2006-03-14
forum: General Help
---

### Post by Jonas_Henricsson on 2006-03-14
What is the corresponding program to First Class ([www.firstclass.com](www.firstclass.com)) in ubuntu? Only Windows and Mac versions are offered on the site. Is there a good program I can use?

Thanks for any reply!

/Jonas

---

### Post by s|k on 2006-03-14
[QUOTE=Jonas_Henricsson]What is the corresponding program to First Class ([www.firstclass.com](www.firstclass.com)) in ubuntu? Only Windows and Mac versions are offered on the site. Is there a good program I can use?

Thanks for any reply!

/Jonas[/QUOTE]
That looks like a complex enterprise online classroom system. You should probably consult with your IT department about finding open source solutions, of which I'm sure IBM or Sun or something other will have. At what kind of scale are you looking at implementing this?

---

### Post by Jonas_Henricsson on 2006-03-14
[QUOTE=s|k]That looks like a complex enterprise online classroom system. You should probably consult with your IT department about finding open source solutions, of which I'm sure IBM or Sun or something other will have. At what kind of scale are you looking at implementing this?[/QUOTE]


I'm looking for this kind of program for personal use. Checking with the IT department might be an idea...

/Jonas

---

### Post by hw-tph on 2006-03-14
Although it has been a while since I used it, there *is* - or at least *was*  - a Linux client for FirstClass, though it was still in beta testing when I used it.

A quick Google search turned up several results, and you can download the rpm's for 7.1 [here](http://firstclass.peoplegroup.fi/client/0000D14E-80000001/00652F37-001E7380-00652F6A). I recall using [alien](http://packages.ubuntu.com/alien) to convert the rpm to a deb and installing that. After some tweaking it worked. I can't say it worked well but it allowed me to participate in the discussions we had at the university.


Håkan

---

### Post by Jonas_Henricsson on 2006-03-19
[QUOTE=hw-tph]Although it has been a while since I used it, there *is* - or at least *was*  - a Linux client for FirstClass, though it was still in beta testing when I used it.

A quick Google search turned up several results, and you can download the rpm's for 7.1 [here](http://firstclass.peoplegroup.fi/client/0000D14E-80000001/00652F37-001E7380-00652F6A). I recall using [alien](http://packages.ubuntu.com/alien) to convert the rpm to a deb and installing that. After some tweaking it worked. I can't say it worked well but it allowed me to participate in the discussions we had at the university.


Håkan[/QUOTE]

Thanks, this was really helpful. I managed to do install the program and I can see it in the opt-folder. I just have one problem now: how do I start First Class?

/Jonas

---

### Post by _linux_ on 2006-04-08
[QUOTE=Jonas_Henricsson]Thanks, this was really helpful. I managed to do install the program and I can see it in the opt-folder. I just have one problem now: how do I start First Class?

/Jonas[/QUOTE]
Run fcc in the terminal if it isn't in the Applications>Internet menu.

---

### Post by nanotube on 2006-04-08
[QUOTE=_linux_]The day Microsoft makes good software is the day they make vacuums.[/QUOTE]

ehrm, just fyi, i think the quote is supposed to be "The day Microsoft makes something that doesn't suck is the day they make vacuum cleaners."
makes much more sense that way. otherwise, what's the connection to vacuums? ;)

---

### Post by Jonas_Henricsson on 2006-04-09
[QUOTE=_linux_]Run fcc in the terminal if it isn't in the Applications>Internet menu.[/QUOTE]

Hmm, I must have made some mistake, because I don't have fcc in my internet menu. But in my opt-folder, I got an installation of first class. Any ideas? Maybe I need to reinstall..?

---

### Post by _linux_ on 2006-04-09
[QUOTE=Jonas_Henricsson]Hmm, I must have made some mistake, because I don't have fcc in my internet menu. But in my opt-folder, I got an installation of first class. Any ideas? Maybe I need to reinstall..?[/QUOTE] I guess some packages don't create shortcuts? Did you try running fcc in the terminal? I'm also trying to run FirstClass on Ubuntu, so I'll tell you if anything works.

---

### Post by Third Thoughts on 2006-04-09
My uni also uses firstclass, though we use a specialized version called learnlink. I tried the linux client, but it broke upon upgrading to breezy. Right now I run it in wine, and its almost perfect. The only time it has trouble is in dealing with attachments. It can't open them directly, so you have to save them to the harddrive and then open them manually.

---

### Post by _linux_ on 2006-04-10
[QUOTE=Third Thoughts]My uni also uses firstclass, though we use a specialized version called learnlink. I tried the linux client, but it broke upon upgrading to breezy. Right now I run it in wine, and its almost perfect. The only time it has trouble is in dealing with attachments. It can't open them directly, so you have to save them to the harddrive and then open them manually.[/QUOTE]Can you tell me how to run it in Wine? I can't get it to work with FirstClass.

---

### Post by Third Thoughts on 2006-04-10
[QUOTE=_linux_]Can you tell me how to run it in Wine? I can't get it to work with FirstClass.[/QUOTE]

I just tried and it seems that both the first class and learnlink installers no longer work under wine. Currently the actual program runs fine for me. And seeing as the ReadMe that came with it says I'm allowed to distribute it as long as no modifications are made, I'll just tar up all the files and let anyone who wants have a go at it on their system. I've poked around a bit and it doesn't look like the version my university has is any different than the normal first class one, considering that they still have the readme in there it seems unlikely that they've made major changes. Just put the FirstClass Folder under Program files on your fake drive. Some how you'll have to get a hold of a settings file somehow, because the setting files I had were related to my school's network. I'd post an example execpt they aren't in plaintext, so I assume that the program generates them somehow.

Here's the link to the file. [http://webdrive.service.emory.edu/users/raswerl/Share/Firstclass.tar.gz](http://webdrive.service.emory.edu/users/raswerl/Share/Firstclass.tar.gz)
I'm hosting it on the space that my school gives me so eventually I'll probably delete it, but it'll be up there for quite a while.

~Andrew s.

---

### Post by _linux_ on 2006-04-11
[QUOTE=Third Thoughts]I just tried and it seems that both the first class and learnlink installers no longer work under wine. Currently the actual program runs fine for me. And seeing as the ReadMe that came with it says I'm allowed to distribute it as long as no modifications are made, I'll just tar up all the files and let anyone who wants have a go at it on their system. I've poked around a bit and it doesn't look like the version my university has is any different than the normal first class one, considering that they still have the readme in there it seems unlikely that they've made major changes. Just put the FirstClass Folder under Program files on your fake drive. Some how you'll have to get a hold of a settings file somehow, because the setting files I had were related to my school's network. I'd post an example execpt they aren't in plaintext, so I assume that the program generates them somehow.

Here's the link to the file. [http://webdrive.service.emory.edu/users/raswerl/Share/Firstclass.tar.gz](http://webdrive.service.emory.edu/users/raswerl/Share/Firstclass.tar.gz)
I'm hosting it on the space that my school gives me so eventually I'll probably delete it, but it'll be up there for quite a while.

~Andrew s.[/QUOTE]
Thanks! It worked great! :D Well, almost. The menus aren't staying open when I click on them. But it's okay. At least it's better than no FirstClass at all.

---

### Post by Jonas_Henricsson on 2006-04-18
[QUOTE=Third Thoughts]I just tried and it seems that both the first class and learnlink installers no longer work under wine. Currently the actual program runs fine for me. And seeing as the ReadMe that came with it says I'm allowed to distribute it as long as no modifications are made, I'll just tar up all the files and let anyone who wants have a go at it on their system. I've poked around a bit and it doesn't look like the version my university has is any different than the normal first class one, considering that they still have the readme in there it seems unlikely that they've made major changes. Just put the FirstClass Folder under Program files on your fake drive. Some how you'll have to get a hold of a settings file somehow, because the setting files I had were related to my school's network. I'd post an example execpt they aren't in plaintext, so I assume that the program generates them somehow.

Here's the link to the file. [http://webdrive.service.emory.edu/users/raswerl/Share/Firstclass.tar.gz](http://webdrive.service.emory.edu/users/raswerl/Share/Firstclass.tar.gz)
I'm hosting it on the space that my school gives me so eventually I'll probably delete it, but it'll be up there for quite a while.

~Andrew s.[/QUOTE]


Woah, works fine here too. You're my hero :)

---

