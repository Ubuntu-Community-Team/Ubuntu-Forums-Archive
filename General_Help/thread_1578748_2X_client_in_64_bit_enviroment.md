---
title: "2X client in 64 bit enviroment"
date: 2010-09-20
forum: General Help
---

### Post by bcdudley on 2010-09-20
I figured I would give this one last shot before I switched my laptop to 32bit. I am running a 2X application server at our office. ([www.2x.com](www.2x.com)). I am trying to run the client on my laptop. It runs great in a 32 bit environment. When I try to run it on my laptop as 64 bit, it does not work. I have loaded the 32 bit libraries, but still no go.

The program will start up and let me configure a connection. I can tell it to connect, but I never get icons from the server. The log files show that it did connect successfully, but it obviously doesn't. 

Any suggestions on this.

Here are the forum responses from the developers web site. It is not really supported, so not much help from them.
[http://www.2x.com/forums/viewtopic.php?f=3&t=4065](http://www.2x.com/forums/viewtopic.php?f=3&t=4065)


Thanks.

---

### Post by efflandt on 2010-09-20
I tried running a 32-bit logmein client plugin in 64-bit Ubuntu by configuring nswrapper (installed by flashplugin-installer for 32-bit flash).  And it sort of half worked in that it came up in the browser with its menues in the left frame.  But it did not show the remote desktop because I believe that uses java, and the plugin could not find 32-bit java in the 64-bit OS.

So I don't know if a 32-bit wrapper would help 2X or if it is looking for 32-bit libs or java that it cannot find.  It only mentions 32-bit Linux versions of the 2X clients.

---

