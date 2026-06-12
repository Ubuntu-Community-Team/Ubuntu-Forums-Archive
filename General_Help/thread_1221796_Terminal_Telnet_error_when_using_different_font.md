---
title: "Terminal: Telnet error when using different font"
date: 2009-07-24
forum: General Help
---

### Post by embolalia1187 on 2009-07-24
At work, I use telnet to access the AIX server. I'm trying to move to Linux where possible. Using the telnet command works fine, with one exception. When I change the font in the gnome-terminal profile, I get a connection closed by foreign host error. I have narrowed it down, and it can only be this that is causing the problem. Is there a reason for this, and can it be fixed? Basically, I need to be able to have the font bigger, and to have that connected to the profile (or to Terminal in general) so that if I close the window and open it again tomorrow, it will still be the same size. Optimally, the text would stretch automatically to fit the size of the window, as it does in the Windows terminal emulator we use.


More detailed description of the problem:
I enter telnet 192.168.1.1 into the prompt. No matter the profile/font size, I get to the login prompt for the AIX server. I log in, and get the usual success messages. If the font is not the default system font at this point, I get the error. Otherwise, I get the normal screen and proceed as usual.

---

### Post by kjohri on 2009-07-24
Please give a clarification. If you set the desired font prior to starting the telnet, do you get an error? Or if you change the font in middle of login or a telnet session, do you get an error. 

Font should have nothing to do with telnet, as the data transmission is text based. I think when you change font in middle of a telnet session, some junk characters might get generated that cause the error.

---

### Post by embolalia1187 on 2009-07-24
Either way. If I change it before I put in the command, at the login prompt, or in a new profile which I then start from a shortcut, it will still happen.

---

### Post by kjohri on 2009-07-24
Well, I think some unwanted characters might be getting generated while using the desired font. You can always debug it by seeing the actual bytes flowing over the network between the telnet client and the remote computer. For example, you can set up Wireshark and see what data is getting transferred and see which character(s) is/are causing the problem.

---

