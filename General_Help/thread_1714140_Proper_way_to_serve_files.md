---
title: "Proper way to serve files"
date: 2011-03-25
forum: General Help
---

### Post by kf6bbl on 2011-03-25
So a little background first. I've been using various distros for the past 12 years and more recently Ubuntu server. I primarily do headless boxes for sharing files, web server, MySQL, mail. What I would like to ask the crowd is for some pointers to current best practices for running Samba with Windows XP clients.

Basically I've kept the security low and used Samba share level security, turned off encrypted passwords, and on the XP client side, done the XP registry hack to make it all work. But now my needs have grown, and recently some hardware died so I'm running Ubuntu server 10.10 now. Samba security defaults have changed, and I feel like my old low tech ways are starting to become a problem. My client machines authenticate slow, and my method of mapping driver letters on XP is not reliable anymore (via DOS batch files).

So whats the better way? The users group size is small (<10), and I don't need atomic control of every file. I am happy with department level security by having many drive letters, but I'm open to suggestions.
Also how should I map the drives to WinXP? My DOS batch file stuff seems caveman-like, but I could never get WinXP to reconnect to drives on login.
And one other Q - Am I making things harder on myself these days by the headless box concept? Seems like a lot of the help out there gives instructions assuming a desktop is installed.

Thanks for help and pointers.
-Bill

---

### Post by kf6bbl on 2011-03-25
Wow, no opinions on this after a day. Well then I should add some details that I forgot to mention.

I network all my Win XP boxes in workgroup mode. Is using a domain controller better? I've never understood the benefits of doing that. Does Samba do a better job at handling users and authentication when using a domain controller?

---

### Post by SeijiSensei on 2011-03-25
Well, first, many of your questions are really Windows ones.  Can't map shares to drive letters?  What if you use "map a network drive"?  Does that work, but "net use" does not?  Can you get your XP boxes to map shares on other Windows machines at boot but not Samba shares?  Even using Windows 7 in a VirtualBox VM on my Ubuntu host I don't have any problem mapping drives from a Samba server or using its networked printer.  Supporting XP clients with Samba has never seemed especially problematic for me.  Nor does authentication seem especially slow.  Am I just lucky?

I'm curious what you mean about the "security defaults have changed."  If you set up an Ubuntu box where all the users have home directories and you've set up passwords with smbpasswd, isn't it possible to map \\server\user pretty much seamlessly?

I think you need to tell us more about the specific problems you're having, and how they arose when you changed versions.

As for your other questions, no, I don't think you need to use a domain with ten workstations, and yes, it's certainly possible to manage the server without a keyboard and monitor.  Just use SSH.

---

### Post by kf6bbl on 2011-03-27
I can map drives, but the method I do it seems dumb, and has not always been reliable.
I use a DOS batch file in the Windows startup group. I've had to add a delay timer because if it runs too early during boot, it fails. Some machines are worse than others, but most have at least 10 seconds of delay before the 'net use...' lines. Yes that's a windows issue.

Second issue is also in the .bat files. I have to put the users username and password in as plaintext. Not sure of this is a WinXP issue or Samba, but even if I have the WinXP username/pass exactly the same, I can't figure out how to pass along those credentials to the server, or the server is rejecting them. So my only solution was to put it in the .bat file.

I can use "map network drive" after browsing to the network neighborhood, providing a username and password after clicking on the server. However I have anywhere from 4 to 8 drives mapped, and I don't want my users mapping drives repeatedly everyday, and for whatever reason they don't reconnect after reboot.

As far as security defaults changing, many years ago on Debian distros, encrypted passwords didn't work or was a pain to setup (can't recall), so the workaround was to do the WinXP registry hack of 'enableplaintextpasswords' so that WinXP and Samba can do the password chat. Now Samba comes with passwords encrypted by default, so I feel like I'm doing something wrong by disabling all that.

---

