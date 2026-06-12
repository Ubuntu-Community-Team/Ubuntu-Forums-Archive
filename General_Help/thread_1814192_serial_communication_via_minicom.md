---
title: "serial communication via minicom"
date: 2011-07-29
forum: General Help
---

### Post by just_abhi22 on 2011-07-29
i had taken two ports (bridged together):COM 6 and COM 7.
 connected COM 6 with hyperterminal (windows) and COM 7 with minicom (Ubuntu)
 
 when i try to connect them,first thing first, i could not send message  from hyperterminal to minicom. WHY?? reverse is possible.**i need two way communication,not one-way.how can i achieve that??[:confused:]("http://ubuntuforums.org/images/smilies/confused.gif")** 
 
 if i close minicom,without typing anything into it, i get a message in HYPERTERMINAL....
 
 **ATZS7=45 S0=0 L1 V1 X4 &c1 E1 Q0** what does this mean?? why it appears always?does it signifies something?
 
 if i type "qwerty", i get message on hyperterminal as
 
 **ATZrty45 S0=0 L1 V1 X4 &c1 E1 Q0** 
 
 this message appears but only when i close minicom. WHY do i need to   close minicom?? in case of two hyperterminals,we could see things   parallel. WHY not in minicom-hyperterminal connection??
 
 **i  can figure out that message "qwerty" is half displayed "rty" in first  line. how could i clear my hyperterminal screen to get a clear and  complete data??**
 
 can any one please explain things in detail. please answer all my querries step by step.

---

### Post by wt8008 on 2011-07-29
It sounds like you have a configuration issue.

What are your settings on Minicom and Hyperterminal? 

The extra random text you see such as ATZ, etc. are control codes for devices such as modems/terminals. This may hint at some misconfiguration if you are seeing that.

---

### Post by just_abhi22 on 2011-07-29
the settings for minicom & hyperterminal : 9600, 8N1, flow control-hardware.
COM6 for hyperterminal and COM 7 (serial port 0) for minicom.

with above setting when i communicate between two hyperterminal,they do very well (bidirectional), but here,minicom dont respond to hyperterminal and hyperterminal responds by giving unusual messages.

---

### Post by Wim Sturkenboom on 2011-07-30
It's not those settings. As said earlier, you have (more than likely unknowingly as I think it's the default) told minicom to communicate with a modem (you can lookup *AT commands* on the web).

Not behind a Linux box at the moment, so can't check what you have to change.

---

### Post by just_abhi22 on 2011-07-30
i have found the said line (highlighted) at initial string in modem setting. but i dont have any idea what to do with it?

how to make things working for me?





abhi@ubuntu:~$ minicom -s




 +--------------------[Modem and dialing parameter setup]---------------------+
 |                                                                            |
 | **A - Init string ......... ~^M~AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0^M   **        |
 | B - Reset string ........ ^M~ATZ^M~                                        |
 | C - Dialing prefix #1.... ATDT                                             |
 | D - Dialing suffix #1.... ^M                                               |
 | E - Dialing prefix #2.... ATDP                                             |
 | F - Dialing suffix #2.... ^M                                               |
 | G - Dialing prefix #3.... ATX1DT                                           |
 | H - Dialing suffix #3.... ;X4D^M                                           |
 | I - Connect string ...... CONNECT                                          |
 | J - No connect strings .. NO CARRIER            BUSY                       |
 |                           NO DIALTONE           VOICE                      |
 | K - Hang-up string ...... ~~+++~~ATH^M                                     |
 | L - Dial cancel string .. ^M                                               |
 |                                                                            |
 | M - Dial time ........... 45      Q - Auto bps detect ..... No             |
 | N - Delay before redial . 2       R - Modem has DCD line .. Yes            |
 | O - Number of tries ..... 10      S - Status line shows ... DTE speed      |
 | P - DTR drop time (0=no). 1       T - Multi-line untag .... No             |
 | Change which setting?       (Return or Esc to exit)                        |

---

### Post by Wim Sturkenboom on 2011-07-30
Took some research, because I never encountered the issue in the past as far as I can recall (6.06, 8.04 and various slackwares). Now on 10.04 and I have indeed the same issue :(

From man minicom, use the -o option
```

minicom -o

```

// EDIT
PS
Use Q to quit. Using X to quit will result in ATZ being send.

---

### Post by grahammechanical on 2011-07-30
Here is a link to the Hayes Command Set which you are using

[http://en.wikipedia.org/wiki/Hayes_command_set]("http://en.wikipedia.org/wiki/Hayes_command_set")

This will help you work out what that Init string is sending as a command.

Regards.

---

### Post by just_abhi22 on 2011-08-04
i found some way to communicate from minicom to hyperterminal, but cud not figure the other way round. i want to use minicom as receiver and hyperterminal as sender, but i could not have that.

for making minicom as sender and hyperterminal as reciever, all we have to do is, CTRL-A then Z, change that setting of both to 9600 8-N-1, NO h/w or s/w flow control. and in configure minicom-->modem & dialing-->delete initial and reset string. also set local echo-ON in setting.
now whatever u type on minicom would be shown on hyperterminal.

but still i cannot do the other way round.i am not able to write on hyperterminal and see on minicom. if any one knows,please help me to get it.
thanks

---

### Post by Wim Sturkenboom on 2011-08-04
Note: this applies to the windows side

Hyperterm might use buffered mode in which case you have to press <enter> before the data is send; does that work?

It's a while ago that I fiddled with it, so can not say for sure if you can (and how to change) the behavior if the above is indeed the problem. Just started hyperterm and by the looks of it you can not influence the behavior.

You might want to install another terminal program in Windows with more options. I know I've used another program in the past, but can't remember the name. Just checked putty and it allows character-by-character transmission according to the help.

> 
Normally, every character you type into the PuTTY window is sent immediately to the server the moment you type it. 

If you enable local line editing, this changes. PuTTY will let you edit a whole line at a time locally, and the line will only be sent to the server when you press Return. If you make a mistake, you can use the Backspace key to correct it before you press Return, and the server will never see the mistake. 


---

### Post by wt8008 on 2011-08-04
Quick question, how did you bridge the two ports together?

With an external cable? Did you check if the cable is working properly?

I am not sure what else would be wrong in your case.

---

### Post by just_abhi22 on 2011-08-04
i am using a "free virtual serial port" s/w (HDD software Ltd.),  that could generates bridged ports (COM6 and COM7, in my case).one port is connected to hyperterminal (COM6) and other port (COM7) is connected to vmware (minicom),for communication.
i have also cheched with putty,giving same problem. I CANNOT type on minicom via hyperterminal but I CAN type on hyperterminal via minicom (serial comm.)

---

