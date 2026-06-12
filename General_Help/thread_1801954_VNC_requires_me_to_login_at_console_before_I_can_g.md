---
title: "VNC requires me to login at console before I can get the VNC screen up on my  pc"
date: 2011-07-11
forum: General Help
---

### Post by jboris on 2011-07-11
Like the subject states I have an issue getting the vnc screen to appear on my PC.
 
I am running 10.0.4 LTS on an HP DL160. I am running Xtightvnc. This server is in our NOC two floors up. I am running Oracle VirtualBox on this server and want to VNC to the Graphical Desktop to adminsiter the server. I want to vnc into the box not the Virtual machines. What happens is this.
1. Reboot Server
2. Login with my user login (either remotely via ssh or at the console) and start the vnc server by doing this:
sudo /etc/init.d/vncserver start
3. Go to my PC and start the RealVNC Viewer and connect to the server. I get the prompt for the Desktop password. Enter the password and screen goes away.
4. Walk the two floors Back on the server I see the sudo password screen where I enter my password.
5. Walk the two floors back to my pc and there is the screen.
 
This is not what VNC is supposed to do but there is probably somne security option not setup or something is wrong. I want to be able to reboot this server when needed and then get back to the Graphical console without all of this. 
 
I have searched High and low and have not one decent How-To or any tutorial that explains how to do this. It seems to me that this is something that is done every day and at sites around the world but I haven't found any documentation that makes sense.
 
Any pointers, help or RTFM reverences to decently written instructions would be a great help.
 
Thanks in advance

---

### Post by CharlesA on 2011-07-11
When I used VNC it never did that.

Are you just using VNC to deal with the virtual machines?

---

### Post by tredegar on 2011-07-11
When you ssh to the server upstairs, try using ```
ssh -X username@server
```
Then when you start vnc the password prompt window should be forwarded to the PC you are sitting at, and save you the walk.

But I start a vnc server on DISPLAY:1 at boot, with this in my **/etc/rc.local**
```
# Start a vnc server for the user install
su - install -c "cd /home/install && vncserver -geometry 1024x768 -depth 24 :1" &
```
I can then connect to it at any time the server is running with
```
vncviewer server:1
``` from my local PC.

Note: this is on my LAN, which has a dedicated firewall. I would not do this over the internet, without running it through a key-authenticated ssh tunnel.

---

### Post by tredegar on 2011-07-11
When you ssh to the server upstairs, try using ```
ssh -X username@server
```
Then when you start vnc the password prompt window should be forwarded to the PC you are sitting at, and save you the walk.

But I start a vnc server on DISPLAY:1 at boot, with this in my server's **/etc/rc.local**
```
# Start a vnc server for the user install
su - install -c "cd /home/install && vncserver -geometry 1024x768 -depth 24 :1" &
```
I can then connect to it at any time the server is running with
```
vncviewer server:1
``` at my local PC.

Note: this is on my LAN, which has a dedicated firewall. I would not do this over the internet, without running it through a key-authenticated ssh tunnel.

---

### Post by jboris on 2011-07-11
Ok. I use a Windows ssh client to access this server and I checked the X11 tunneling feature. I can connect to the server via ssh this way. I then connected with the RealVNC Viewer to display 1 . I got the password screen and was able to login but I am not sure fi this will work when I reboot the server next time. I edited my /etc/rc.local file and will see if this will rerstart at next boot time. It is a shame that I just can't have the VNC Server running and connect directly to it. This extra step is annoying and will possible cause me issues through outr vpn setup here but at least I can connect and not travel the stairs. My knees can't take it.
 
Thanks for the quick responses.

---

### Post by tredegar on 2011-07-11
> It is a shame that I just can't have the VNC Server running and connect directly to it. 
You can. With that line (obviously you'll have to change *install* to your *username*) in **rc.local**, a VNC server will be started at every boot. Nobody even needs to be logged in. It just sits there, waiting for a connection.

Connect to it and use it.
How you connect to it with windows, I do not know, but you seem to.
When you have finished with it, just _close the vnc window_. Do _not_ choose logout, or the vnc session will die.

---

