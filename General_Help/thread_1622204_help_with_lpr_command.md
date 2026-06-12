---
title: "help with lpr command"
date: 2010-11-15
forum: General Help
---

### Post by darthpenguin on 2010-11-15
Hi All.

I have an Ethernet printer plugged into my home router on the upper level of my house. In that same room i have a Mac Mini. Sometimes I like to connect to my Ubuntu machine downstairs to print some files since I'm at the Mac anyway. I use to do this via VNC which was always a bit slow (and, since the update to ubuntu 10.10, Mac's "Screen Sharing" stopped connecting to Ubuntu all together). I can also do this through file sharing via SMB (that's how i do it now). But I love terminal commands and (Mac or Linux) I prefer to use the shell. I thought I'd try to ssh into Ubuntu from the Mac and use the lpr command to print documents (downloaded docx format). The problem is I just got gibberish. Each page printed with 1-2 lines (at the top of the page) of random ASCII text. What went wrong? how do I use the lpr command?

Thank you for any help.

---

### Post by wt8008 on 2010-11-17
Hello

Based on my memory, lpr can only print pdf, ps, and plain text files. You should save the document as a PDF first. 

I think the proper setup you should do is to setup the printer locally on your Mac.

---

### Post by darthpenguin on 2010-11-17
Really? I didn't know that. Thanks.

Is there another command that could print docx, odt, etc.? or maybe a command that converts such files to ps or pdf so that i may use the lpr command?

What do you mean "setup printer locally to mac". I like it plugged into the router because the router never turns off. If it's plugged into the mac and the mac is shutdown the printer is no longer available to the network. besides, how it's hooked up has no baring on my problem i think.

---

### Post by wt8008 on 2010-11-17
I do not know of any command that works for those files.

I am not sure why you didn't add the network printer directly on your mac.

---

### Post by darthpenguin on 2010-11-17
Hmmm. that's a shame. if i want to print files remotely I guess I can just access the files via smb. Of course I can't open odt (or other openoffice documents) on the mac so in those cases i'll need to walk down to the physical ubuntu machine in the basement to print then return to the printer to get the print outs. at least I get exercise. :).

> I am not sure why you didn't add the network printer directly on your mac.

There seem to be a misunderstanding here. It's not important I guess, but... The Mac and the router are in the same room weather I plug the printer into the router or the Mac makes no difference. The printer would still be shared to every machine on the network and it would still be a whole 2 floors away from some machines (including the ubuntu machine and, at times, the laptop). Either way I'd still need a solution for remotely printing any documents stored on any machine at any time from any client. That would be nice. I only connect the printer to the router because it never powers off and, therefor, the print server and printer are always available (24/7) and never goes down. That's all.

---

