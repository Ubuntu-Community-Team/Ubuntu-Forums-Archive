---
title: "Close my terminal but keep matlab running on a remote Ubuntu"
date: 2012-03-04
forum: General Help
---

### Post by nickxtsui on 2012-03-04
hi Folks:
I am new to Ubuntu, so please forgive me if you think my question is dumb.

I am running Matlab on a remote Ubuntu from my laptop.  My Matlab program takes hours, or even days to run. So the best way is to let it run on the remote Ubuntu even if I logout my connection with it. 

I was told screen command can do that. So here is what I did:

1. Connect to the remote Ubuntu using butty, initiate a new screen session, and start Matlab.
2. Let the Matlab scrip run. (when Matlab script is running, its interface is shown on my laptop)
3. Detach, and then logout the screen session.
4. Close butty (of course, the Matlab windows on my laptop were also gone)
5. Reconnect to the remote Ubuntu, and re-attach the screen session.

But, no Matlab was running! 

So, how do I run my Matlab script on that remote Ubuntu with my connection to that server is closed?

Thanks a lot. Any suggestion is appreciated.

---

### Post by papibe on 2012-03-04
Hi nickxtsui. Welcome to the forums!

I use screen a lot to do very similar tasks.

It looks like you are doing the right thing. Could you post the actual commands you are using to create, de attach, and re atthach the screen?

Regards.

---

### Post by nickxtsui on 2012-03-04
> **papibe said:**
> Hi nickxtsui. Welcome to the forums!

I use screen a lot to do very similar tasks.

It looks like you are doing the right thing. Could you post the actual commands you are using to create, de attach, and re atthach the screen?

Regards.

hi [papibe]("http://ubuntuforums.org/member.php?u=774785"). Thanks!

Here is what I did. 
1. Using putty terminal to login to Ubuntu server, and typed:
screen

2. typed:
matlab

3. After I typed "matlab" in step 2, then Matlab windows poped up (I use X11 forwarding). Then I started running the Matlab script. The way I ran Matlab script was I simply highlighted all code in .m file, then right click mouse to select "Evaluate Selection". Then the Matlab was running. If I don't do anything to disturd, it could run for days. Then I went back to putty terminal, simple press Ctrl a, then Ctrl d.

4. After Ctrl a, Ctrl d, the putty terminal showed "[detached from 4712.pts-18.buffy]". Then I typed:
exit

5. After I typed exit in step 4, the putty terminal showed "logout". Then I clicked the red cross on the putty terminal to close it. Of course the running Matlab windows were gone as well.

Anything you think I was wrong? Thanks a lot.

---

### Post by papibe on 2012-03-04
I'm not familiar with Metlab, but for what I understood 'screen' is really the problem here.

The GUI you run on the client side needs the ssh connection alive in order for the X11 forwarding to work. When you exit/logout you are effectively killing the communication between Metlab on the server and the Metlab GUI on the client side.

Are they any native Windows Metlab clients? May be there's a way set the server side to serve a port, and then configure the client to connect to that port. If so, then 'screen' would let you keep Metlab running serving that port.

Hope it helps, and tell us how it goes.
Regards.

EDIT: btw, to de attach a screen the command is 'Ctrl+a' and then just 'd'.

---

### Post by nickxtsui on 2012-03-04
> **papibe said:**
> I'm not familiar with Metlab, but for what I understood 'screen' is really the problem here.

The GUI you run on the client side needs the ssh connection alive in order for the X11 forwarding to work. When you exit/logout you are effectively killing the communication between Metlab on the server and the Metlab GUI on the client side.

Are they any native Windows Metlab clients? May be there's a way set the server side to serve a port, and then configure the client to connect to that port. If so, then 'screen' would let you keep Metlab running serving that port.

Hope it helps, and tell us how it goes.
Regards.

EDIT: btw, to de attach a screen the command is 'Ctrl+a' and then just 'd'.

Hey papibe, thanks a lot first.
So are you saying to let the script running on the serve side, there should not be any graphic window from that program on the client side? 
Perhaps I can run Matlab  on the serve without graphic interface. In that case there might not be any Matlab windows on my laptop. Is that what you mean? Thanks.

---

### Post by Khayyam on 2012-03-04
You should probably run 'nohup' or 'disown' ... as then it won't be connected to the tty and you can exit, no screen session should be needed.

```
% ssh user@host.domain.tld
% nophup matlab <options> file &
% exit
```or using 'disown'
```
% ssh user@host.domain.tld
% matlab <options> file
^z
% bg %1
% disown -h %1
% exit
```There is no way to "re-own" (or re-attatch) the process so it means the job can't be 'managed', so to speak, but you can kill if need be (as you are still the owner of the PID).

I should also mention [reptyr]("https://github.com/nelhage/reptyr") which can be used in conjunction with screen.

HTH ... khay

---

### Post by Khayyam on 2012-03-04
> **nickxtsui said:**
> So are you saying to let the script running on the serve side, there should not be any graphic window from that program on the client side? Perhaps I can run Matlab  on the serve without graphic interface. In that case there might not be any Matlab windows on my laptop. Is that what you mean?

Yes, I think s/he does ... you didn't say you we're forwarding X11, which makes my suggestion of nohup or disown non-options.

best ... khay

---

### Post by nickxtsui on 2012-03-04
> **Khayyam said:**
> Yes, I think he does ... you didn't say you we're forwarding X11, which makes my suggestion of nohup or disown non-options.

best ... khay

So initiate a new screen session, then running matlab script using a command line, then detach the screen session. Then pick up the session some time after. Is it how it is operated? Thanks.

---

### Post by Khayyam on 2012-03-04
> **nickxtsui said:**
> So initiate a new screen session, then running matlab script using a command line, then detach the screen session. Then pick up the session some time after. Is it how it is operated? Thanks.

Well, that's what you were doing initially, no? Basically, your trying to detatch an X11 forwarded application that needs the ssh session open as that is used to forward the traffic.

I'm not a matlab user but I had thought that matlab could be run as a number cruncher without the GUI. Is this what your trying to do **or** do you want to forward the GUI to your laptop? With the former you should be able to 'nohup' or 'disown', and the latter not.

HTH ... khay

---

### Post by nickxtsui on 2012-03-04
> **Khayyam said:**
> Well, that's what you were doing initially, no? Basically, your trying to detatch an X11 forwarded application that needs the ssh session open as that is used to forward the traffic.

I'm not a matlab user but I had thought that matlab could be run as a number cruncher without the GUI. Is this what your trying to do **or** do you want to forward the GUI to your laptop? With the former you should be able to 'nohup' or 'disown', and the latter not.

HTH ... khay

The best I hope is, I can edit remote Matlab scripts on my laptop using its GUI. Then after I start running the remote Matlab scripts from my side, I can close the Matlab GUI and the connection from my side. Then I can shut down my laptop. But the remote Matlab scripts are still running. 
Seems it is not possible.
Thank you very much.

---

### Post by nickxtsui on 2012-03-04
OK, here is how I dealt with it.

I changed the matlab code, such that no figures will pop up.
Then I connected to the remote Ubuntu. Then I quit X11 forwarding. Then I initiated a new screen session. Then I started matlab from console, putty terminal. Then I ran matlab script. Then I detached the screen session. Then I logout.

I think it worked. Thanks everybody.

Just no figures, save your data somewhere, you can reload it and re-plot later on.

---

### Post by Khayyam on 2012-03-04
> **nickxtsui said:**
> I changed the matlab code, such that no figures will pop up.Then I connected to the remote Ubuntu. Then I quit X11 forwarding. Then I initiated a new screen session. Then I started matlab from console, putty terminal. Then I ran matlab script. Then I detached the screen session. Then I logout. I think it worked. Thanks everybody.

OK, well if it works out as expected you should then [mark the tread as [SOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by phaed on 2012-03-05
The only way that I was able to make it keep running is in screen / tmux / byobu without the GUI.

matlab -nodesktop -nosplash -nojvm

---

### Post by nickxtsui on 2012-03-05
> **phaed said:**
> The only way that I was able to make it keep running is in screen / tmux / byobu without the GUI.

matlab -nodesktop -nosplash -nojvm

Thanks
Will try that.

---

### Post by nickxtsui on 2012-03-05
> **Khayyam said:**
> OK, well if it works out as expected you should then [mark the tread as [SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

Let me try that. Thanks.

---

### Post by andrescodas on 2012-10-08
If I run `ssh -X [email]me@server.com[/email]` I'm able to run matlab gui, and in addition with the screen command I can keep it running after logout.

Do you know if in adition after logging out if I can logging again and recover the last GUI session ??

I have an application that creates figures, and I want to be able to see them after logout and login again, just like rdp in windows but this time using ssh.

any idea?

---

### Post by steeldriver on 2012-10-08
I do that with a vnc session tunneled over ssh to my work for things like MATLAB :-

- ssh log in, setting up an ssh tunnel on 5900 + n

- start a vncserver server session on display :n 

I then just leave the session running and can reopen the tunnel / reconnect the vnc client anytime

---

