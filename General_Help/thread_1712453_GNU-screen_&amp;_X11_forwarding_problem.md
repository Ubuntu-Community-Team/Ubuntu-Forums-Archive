---
title: "GNU-screen &amp; X11 forwarding problem"
date: 2011-03-22
forum: General Help
---

### Post by gbuntu127 on 2011-03-22
Hello, ubuntuers :)

I started running a program on a server using ssh with -X (also -Y) forwarding on a remote server. Since the program takes 4-5 hours to finish, so I use **GNU-screen** to start a new session and leave it running detached, I can close terminal from my end with no problem. This worked perfectly several days ago. 

However, these two days whenever I setup and detach a session for the program to run on the server, and then close my terminal on my local machine, it is found that the program run on the server is failed with the following message:

[B]Fatal IO error 0 (Success) on X server localhost:11.0
Unable to initialize gtk, is DISPLAY set properly[/B]

I don't know what went wrong here, [a similar problem]("http://tinyurl.com/4ken2ve") from google showed quite similar situation, but not a working solution. 

The only change I made to the server recently is to generate a ssh key and ssh-copy-id my key to the server's ssh authorized_keys.  I wonder if a restart on the server can reset the problem, but it is a share server and I do not own the root right. 

Thanks in advance for helping.


**Edit**
I have also tried with nohup Program & on the server, strangely when I logged out from server (close the terminal), it prompted that 
**"There is still a process running in this terminal. Closing the terminal will kill it"** 

Isn't this weird? I mean that nohup is used to run program at background, how could it be still attached to my current terminal? I do see the program running with a new PID. Does it mean that it somehow still attaches to my current terminal?

---

