---
title: "enabeling X-Windows in 10.04"
date: 2010-05-12
forum: General Help
---

### Post by mab1376 on 2010-05-12
I have a 10.04-server running and I installed the ubuntu-desktop and would like to know how to enable X-Windows so I can connect with XWin from a windows workstation.

If anyone has a procedural document, that would be great.

Thanks in advance!

---

### Post by TheFu on 2011-03-07
> **mab1376 said:**
> I have a 10.04-server running and I installed the ubuntu-desktop and would like to know how to enable X-Windows so I can connect with XWin from a windows workstation.

If anyone has a procedural document, that would be great.

Thanks in advance!

None of these instructions are specific to any particular release of Ubuntu. Any Debian based system will work the same.  X/Windows has been around 20+ yrs and most of these techniques have not changed over that time.

So this is months later and you've probably learned that X-Windows is a client/server architecture that works backwards of most C/S systems.  For X/Windows, the "server" runs on your desktop and the "client" program runs on the remote machine (usually what we consider the server, but not in this case). Read more here [https://secure.wikimedia.org/wikipedia/en/wiki/X_Window_System](https://secure.wikimedia.org/wikipedia/en/wiki/X_Window_System) In ubuntu, using the package manager to load any X/Windows client program will pull in the required X/Client files.  


[LIST]
[*]sudo apt-get install xterm
[/LIST]
Would be my choice to install on the remote machine to automatically pull all the needed client X/Windows libraries.

That was easy. Now for the harder part, the X/Server on MS-Windows. You need to install an X/Server program on your Windows desktop. There are lots of options for this - commercial ($300) versions of X-Windows for MS-Windows or free ones.  For me, it was easiest to run a full Linux desktop inside VirtualBox, because it has the best X/Server available, IMHO.  Cygwin/X or Xming are MS-Windows free implementations and there are others. Google for "free x-server win32" to find more information.  Then you'll need to figure out how to setup all of these to make the X/Windows client/server connection. They all do it a little differently.

Honestly, the easiest way to setup an X/Server is to run a Linux desktop OS.  **The remote server DOES NOT NEED THE X/SERVER programs at all**.

Once you have an X/Server running on your desktop and appropriate X-Client programs running on some remote server, then you just need to make that remote connection and start the client machine. X/Windows has some weenie security built-in that you either need to work with or you can, more easily, create an X/Windows tunnel with ssh by using 

[LIST]
[*]ssh -Y username@remote prog
[/LIST]
So, from a Linux desktop machine connecting to a remote server, 

[LIST]
[*]ssh -Y user01@rem-serv  xterm
[/LIST]
wait a few seconds and the 'xterm' will be displayed on your PC.   Here are more details [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) on running remote applications.

I hope this helps.

---

