---
title: "Mp3 permissions"
date: 2006-05-02
forum: General Help
---

### Post by astronerd on 2006-05-02
Hi everyone, I just ripped an MP3 CD to my hard drive and now all the songs have a little padlock icon on them.  Im assuming this means limited permissions on them.  How can I change this to regular permission like all the other MP3s I have?  I have root access and use to box alone, so I dont need to have them limited.  
Thanks, 
Charles

---

### Post by jazzmuzik on 2006-05-02
You can right click on the mp3, select Properties, and Permissions. Normal permissions on a file like this would be be
Owner: r/w
Group: r
other: r

Also, the file owner should be you

---

### Post by astronerd on 2006-05-02
Thanks, but Is there a way to do this on the command line?
  here is what I would try...(its probably waaay off)

chmod -rwx-----  /folder/music/*.mp3

Is this even close?  Just trying to learn the terminal too...
Thanks again, 
Charles

---

### Post by gunderwood on 2006-05-02
chmod -R 644 /path/*.mp3

or 

chmod -R u+w /path/*.mp3

---

### Post by nanotube on 2006-05-02
[QUOTE=astronerd]Thanks, but Is there a way to do this on the command line?
  here is what I would try...(its probably waaay off)

chmod -rwx-----  /folder/music/*.mp3

Is this even close?  Just trying to learn the terminal too...
Thanks again, 
Charles[/QUOTE]
gunderwood gives the right answer. but, yes, it's close - good logical thinking. :)
for the future, if you want to learn more about some command, there is "man". so you can try "man chmod" to learn more about chmod. man is the first step when you have doubts about the proper usage of some command.

---

### Post by jazzmuzik on 2006-05-02
[QUOTE=astronerd]Thanks, but Is there a way to do this on the command line?
  here is what I would try...(its probably waaay off)[/QUOTE]

Ha. I started writing a command line solution but decided against that because the padlock shows up in nautilus...

Do what gunderwood suggests.

---

