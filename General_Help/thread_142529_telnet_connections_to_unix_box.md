---
title: "telnet connections to unix box"
date: 2006-03-10
forum: General Help
---

### Post by n.arciss.us on 2006-03-10
When I try:
```
telnet 192.168.0.9
```

I get:
```
Trying 192.168.0.9...
Connected to 192.168.0.9.
Escape character is '^]'.

SCO OpenServer(TM) Release 5 (hijohn) (ttyp4)

login: rx
LOGIN: All licenses are in use.
WARNING: All licenses are already in use. To purchase additional
         licenses, please contact your SCO supplier.
Last successful login for rx: Fri Mar 10 15:12:05 2006 on ttyp6
Last unsuccessful login for rx: NEVER

                          SCO OpenServer(TM) Release 5

                  (C) 1976-1998 The Santa Cruz Operation, Inc.
                  (C) 1980-1994 Microsoft Corporation
                              All rights reserved.

                        For complete copyright credits,
                   enter "copyrights" at the command prompt.

                                            #     #
                             #####    ####  #     #
                             #    #  #    # #     #
                             #    #  #      #     #
                             #####   #       #   #
                             #       #    #   # #
                             #        ####     #

                        #     #         ########
                        #     #                #
                        #     #                #
                        ########        ########
                              #   ###          #
                              #   ###          #
                              #   ###   ########
                       This product brought to you by
     #####    #   #   #####  ######   ####   #    #     #    #    #   ####
     #    #    # #      #    #       #    #  #    #     #    ##   #  #    #
     #####      #       #    #####   #       ######     #    # #  #  #
     #    #     #       #    #       #       #    #     #    #  # #  #
     #    #     #       #    #       #    #  #    #     #    #   ##  #    #
     #####      #       #    ######   ####   #    #  ,  #    #    #   ####

Terminal Definition for xterm NOT FOUND!
Connection closed by foreign host.
```

This connections works on a windows box but I can't see to get through on U..tu.

Any ideas?

---

### Post by astyanax on 2006-03-10
I'm assuming you are trying to telnet to a machine on your own private network.  It sounds like a permissions issue.

Are you booting into Windows on the same box that Ubuntu is installed when you try to telnet or is it a different system?

If is a different system, can you switch the network cable on the Windows box with the cable on the Ubuntu box and try it?  If it works, then you know it's definitely a rights issue with the router and not Ubuntu.

---

### Post by n.arciss.us on 2006-03-10
[QUOTE=astyanax]
Are you booting into Windows on the same box that Ubuntu is installed when you try to telnet or is it a different system?[/QUOTE]

I am trying on a laptop with dual boot XP/U..tu

---

### Post by astyanax on 2006-03-10
I didn't read that right.  My bad.  I didn't realize that it was actually connecting in Ubuntu.

What it looks like is xterm doesn't have a terminal definition for SCO OpenServer or you need to specifically pass the definition in at the command line.

I'm not familiar with xterm definition files, but there are other terminal emulators that you can install and try.

I'm sorry I can't be of more help.

---

### Post by lamego on 2006-03-10
Setting the TERM variable to vt100 should be enough:
```
  export TERM=vt100
```
then login, xterm supports vt100 and SCO should also support it...

---

### Post by n.arciss.us on 2006-03-10
[QUOTE=lamego]Setting the TERM variable to vt100 should be enough:
```
  export TERM=vt100
```
then login, xterm supports vt100 and SCO should also support it...[/QUOTE]


just to clarify ??:

```
telnet 192.168.0.9 export TERM=vt100
```

---

### Post by KnottyMan on 2006-03-10
no

export TERM=vt100

then 

telnet 192.168.0.9

---

### Post by n.arciss.us on 2006-03-11
ok ... thanks... I'll let you know how it works.

---

### Post by n.arciss.us on 2006-03-13
Thanks Knotty that worked.

---

