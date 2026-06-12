---
title: "Ubuntu server problem"
date: 2012-06-23
forum: General Help
---

### Post by bender1 on 2012-06-23
I have ubuntu server on a dedicated pc.I am trying to run a windows application using wine through putty.This is the error i get.```
err:module:import_dll Library SSLEAY32.dll (which is needed by L"Z:\\root\\wow\\LIBMYSQL.dll") not found
err:module:import_dll Library LIBEAY32.dll (which is needed by L"Z:\\root\\wow\\LIBMYSQL.dll") not found
err:module:import_dll Library LIBMYSQL.dll (which is needed by L"Z:\\root\\wow\\authserver.exe") not found
err:module:import_dll Library LIBEAY32.dll (which is needed by L"Z:\\root\\wow\\authserver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\root\\wow\\authserver.exe" failed, status c0000135
root@ns236412:~/wow# Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window

```

The program i am tryig to run opens in windows a run window in which the log appear.

---

### Post by HiImTye on 2012-06-23
> **bender1 said:**
> root@ns236412:~/wow# Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
make sure you're sshing into it with -X

---

### Post by bender1 on 2012-06-23
I am using putty to connect.

---

### Post by HiImTye on 2012-06-23
putty is an ssh client.. am I missing something?

---

### Post by HiImTye on 2012-06-23
here, read this for some instructions on how to use X
[http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html](http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html)

---

### Post by bender1 on 2012-06-23
> oot@ns236412:~/wow# Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window



I want it to run in putty,to show the log in terminal.like in windows command prompt

---

### Post by HiImTye on 2012-06-23
those instructions I linked are for putty.

X is the windowing system that Unix/Linux uses.
PuTTY is an SSH client.
SSH has the capability of using X windows using the -X switch.
PuTTY has the capability of enabling X windows using those instructions.

follow the instructions.

---

### Post by bender1 on 2012-06-23
> 
root@ns236412:~# $ xclock &
[1] 12071
root@ns236412:~# $: command not found



This is what i get when i try to run the test to see if it works.

---

### Post by HiImTye on 2012-06-23
the test isnt important, try your other command again now that X is enabled

---

### Post by bender1 on 2012-06-23
> 
err:module:import_dll Library SSLEAY32.dll (which is needed by L"Z:\\root\\wow\\LIBMYSQL.dll") not found
err:module:import_dll Library LIBEAY32.dll (which is needed by L"Z:\\root\\wow\\LIBMYSQL.dll") not found
err:module:import_dll Library LIBMYSQL.dll (which is needed by L"Z:\\root\\wow\\authserver.exe") not found
err:module:import_dll Library LIBEAY32.dll (which is needed by L"Z:\\root\\wow\\authserver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\root\\wow\\authserver.exe" failed, status c0000135
root@ns236412:~/wow# Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window


Same as before

---

