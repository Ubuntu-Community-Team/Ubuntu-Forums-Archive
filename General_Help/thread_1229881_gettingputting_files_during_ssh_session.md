---
title: "getting/putting files during ssh session"
date: 2009-08-02
forum: General Help
---

### Post by ooobooontooo on 2009-08-02
Hi,

I was wondering if there was a way to get/put files during a ssh session. I know I could just open up another terminal and scp/sftp, but I would like to know if there's a way to get/put using the ssh session I already have. Thanks in advance.

---

### Post by nothingspecial on 2009-08-03
I`m not really sure what your asking here. You want to do multiple things from one ssh terminal? 

Have a look at screen which supports sdifferent sessions in the same terminal.

and/or

dvtm which will split your terminal screen into different windows in a tiling manner.

```
sudo apt-get install screen dvtm
```

---

### Post by t0p on 2009-08-03
> **ooobooontooo said:**
> 
I was wondering if there was a way to get/put files during a ssh session. I know I could just open up another terminal and scp/sftp, but I would like to know if there's a way to get/put using the ssh session I already have. 

Sorry, but I think scp is it.  If you have a problem with having more than 1 ssh session running at a time, you could always end the current ssh session, do your scp stuff, then start a new ssh session.  I suppose...

**EDIT:** A thought.  I've never done this, so I have no practical experience.  But could you go to **Places > Connect to Server**, start ssh connection there, then cut-and-paste files from the remote server window to your local Desktop (or wherever)?

**RE-EDIT:** It appears that you *can* do this.  To test my theory, I used **Places > Connect to Server** to start a graphical ssh connection to a remote machine on which I have a shell account.  Once this connection was established, ubuntu reported it as a sftp connection.  But I don't see as that makes much difference (netstat reports it as a ssh connection regardless of what gnome is telling me).  And yes, I was able to drag files from the remote server window to the local Desktop window with no difficulty.

---

### Post by ooobooontooo on 2009-08-03
@nothingspecial
Sorry for being unclear. I have a remote box and I often ssh into it to configure files and all that. I also often have to get/put files from/to the remote box. Right now, I'm doing this by opening up another ssh session using scp. I was wondering if there was a way to do this using the existing ssh session that I have.

@t0p
Thanks for your advice and answer. I think that solves it...unfortunately, opening up a gui to use ssh is probably slower than opening another terminal (in terms of moving mouse to click and all that)....blah, but thanks for your answer.

---

### Post by nothingspecial on 2009-08-04
Did you have a look at screen and dvtm?

```
sudo apt-get install dvtm
```

on your headless box.

ssh into it then type ```
dvtm
```

Press Ctrl+G then C to create a new window within the same terminal.

I don`t know if there is a maximum or not.

Ctrl+G then X will close the "window" you are using (ie the one with the flashing cursor) ... is that what they call focused.

Screen comes installed with ubuntu 9.04.

Type ```
screen
```

Like dvtm each command starts with a 2 key combination. With screen it is Ctrl+A.

Ctrl+A then a number 0-9 will switch between screen windows. So open screen on your server Ctrl+A then 2 

```
scp -rv whatever/file/you want/to/move you@your.ip
```

Then Ctrl+A 1 and get on with your editing. When you want to check the progress of your file transfer just Ctrl+A 2.

Even better than that if you press Ctrl+A then D screen will detatch that session leaving it running so you can start that file transfer, detatch, logout, drive 500 miles away and log back in to your "server" from a different computer. Then type ```
screen -r
``` and you can see how your file transfer is getting on. Very useful for large torrents, downloads, mass file conversions etc.

Of course if you have dvtm and screen running on both machines doing loads of jobs with multiple windows and sessions things can get confusing.....but it`s fun.

---

