---
title: "Where to get help on setting up WINE &amp; Ubunto"
date: 2006-04-27
forum: General Help
---

### Post by kerry165 on 2006-04-27
I am a newbie to Ubuntu (a day of real hands-on so I am on a steep learning curve here). I did work on Unix internals in the 80's (more in the earlier part when it first went commercial) but done nothing since. I have just set up a machine to play with the environment and am amazed at how the technology has moved on in this arena. But that's another issue.

I wanted to test what I can and cannot do in the Ubunto environment wrt running a windows app.

I have set up the PC. (Single user at the moment). The update program says it is uptodate.

I added the WINE package from a link on [http://www.winehq.com](http://www.winehq.com) and it is installed (0.9.12). Now I start to struggle to find info.

Step 1 is just to get the app to work cleanly.

App is an interpreted program and is run e.g.:
c:\theprogs\system\interpret.exe start.prg
starting in the application directory
j:\theprogs

i.e. in the windows environment the interpreter and programs reside on the local machine with the datafiles on a mapped drive.

Hunting for sources of docs I have found out elementary info on
wincfg
(I set and created a "J:" drive her

wine regedit
I created the Environment key here with a Temp & Path setup
The Path has c:\theprogs\system included

I can start the app if I say in a terminal session

     cd /mydata/hostfiles      (this is the folder that is mapped to J:)
     sudo interpret.exe start.prg

If I put it in a script I get the popup box asking me how I want to run it. If I choose "Run" it just exists (i.e. it is to quick for me to see the message). I I choose "run with terminal" then it starts ish!!!

I would like to know.

1. Can I start the app from a script without the "prompting"
2. Are there docs explaining in simple terms (so I can get it running quickly) how / what permissions need to be set so that I can run the app without "sudo"
3. Can Ubunto/Wine allow multi users (via thin clients) to run the app in the same way as Term Services/Citrix does?
4. Can Ubunto mount a shared folder residing on a Win2K/Win2003 Server? (so I can "map" to it under WINE

I think that should keep me going for a few days.

Many thanks

Kerry

---

### Post by mjm115 on 2006-04-27
[Here]("https://wiki.ubuntu.com/Wine") is something to get you going.  I'm sure if you search the forums, you can find a little more detail for what you're looking for.

---

### Post by kerry165 on 2006-04-27
Thanks for that. 
I have been searching but all that I have found at the moment doesn't relate to my questions. But it all adds to the learning pot!

Kerry

---

### Post by kerry165 on 2006-04-27
Still searching through the posts as best I can. Following up with my initial key questions

1. Can I start the app from a script without the "prompting"
Still stuck here. In the standard Ununto login (not had time to read all the variants yet) I have created a text file and set mode +x. When I go to run the script it asks me which option? (terminal, display, run etc.). Can I set it to just run the script?  :confused: 

2. Are there docs explaining in simple terms (so I can get it running quickly) how / what permissions need to be set so that I can run the app without "sudo"
Played around with permissions and got a working environment. Still not convinced it is a good solution and am still looking for docs that would give me somone else's perspective. :-k 

3. Can Ubunto/Wine allow multi users (via thin clients) to run the app in the same way as Term Services/Citrix does?
Found a thread that I hope will really help me here referring to installing VNC server and xinetd. I think it uses VNC server in a slightly different context than I am used to. I am after the ability to use a remote login to create a user session on the Linux server to run my apps on the server without the need to take over an existing logged in session i.e. to create a login session at conenction.
I believe [http://ubuntuforums.org/showthread.php?t=122402&referrerid=101446](http://ubuntuforums.org/showthread.php?t=122402&referrerid=101446)
will tell me how. I will find out tomorrow.  :D 

4. Can Ubunto mount a shared folder residing on a Win2K/Win2003 Server? (so I can "map" to it under WINE
Found some postings (mentioning different tools as well) on this subject with some success. Not exactly the most consistent results, but I testing if this is down to ignorance at this stage. Seems very slow though.
:confused: 

Still it is moving on

---

