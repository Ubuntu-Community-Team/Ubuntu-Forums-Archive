---
title: "Trying to use Ubuntu/Ubuntu Studio 10.04 at the Toronto Public Library?"
date: 2010-05-20
forum: General Help
---

### Post by MIJ-VI on 2010-05-20
August 12th, 2008 - 05:42 pm ET by Jesse Dorland

"Few months ago I post a wifi connection problem. For some reason I was unable to log into Toronto Public Library Wifi's network. Mr. Helge
provided an excellent solution to my problem. You see TPL is running
their sever on nt, and I needed Winbind package for that. Now I am
able surf internet on my lovely Linux distro :)

I reposting the solution here incase someone is also having the same
problem.

If spyders.local is a local network address, it might be a problem (or
lack) of proper name lookup.

Try enabling WINS name lookup as additional to standard DNS.

In Ubuntu/Debian you would do this by installing the winbind packages,
together with samba I think.

Once winbind is up and running, add "wins" to the end of the "hosts:"
line in /etc/nsswitch.conf

Like this:
***** /etc/nsswitch.conf ******

hosts files dns wins

*******************************

You might need to restart your network or reboot, but IIRC it usually
works right away.

-

Thank you Helge"

[http://us.generation-nt.com/toronto-public-library-help-171139901.html](http://us.generation-nt.com/toronto-public-library-help-171139901.html)

--------

I followed Jesse's relayed instructions but ran into a snag under Ubuntu 10.04 which refused to connect to the T.P.L.'s home page:

Here is the way /etc/nsswitch.conf originally looked on my PC...

[FONT=Courier New]# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis[/FONT]

...and here's the way it looked when I finally got it to work:

[FONT=Courier New]# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
[/FONT]
BTW. I first ran [FONT=Courier New]shares-admin[/FONT] in Terminal (to install Sharing services for Windows, and Unix machines <-- why not? :)) and then edited /etc/nsswitch.conf by using this command in Terminal...

[FONT=Courier New]gksudo gedit /etc/nsswitch.conf[/FONT]

...and then rebooted.

I also found that I had to temporarily *disable the NoScript add-on I'd installed in Firefox until after I had succeeded in reaching Google via Spyders-->T.P.L.'s home page.

*I expect there's a way to add Spyders to NoScript's 'white list' but I haven't figured out how to do that yet.

Oh yeah. Don't forget to make a backup copy of the nsswitch.conf file (by dragging it out onto the desktop) before editing it.

--------

I hope this post will spare other Ubuntu/Ubuntu Studio 10.04 newbies the Toronto Public Library log on headaches I went through for I expect that the T.P.L. isn't the only public library system using a Windows NT server and an IT security company similar to [Spyders]("http://spyders.ca/").

---

