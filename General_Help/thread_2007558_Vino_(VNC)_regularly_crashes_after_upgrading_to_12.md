---
title: "Vino (VNC) regularly crashes after upgrading to 12.04... Workaround?"
date: 2012-06-20
forum: General Help
---

### Post by willis11of12 on 2012-06-20
So for the past month now, I continue to see Vino-server crash, which isn't a big deal when I am physically there to restart it, but when I am away I have no way to restart it!  

I am wondering if anyone knows of an alternative that has worked well for them on Ubuntu 12.04, or would you suggest I use an earlier Ubuntu instead?  

I recently installed an earlier version on a separate hard drive and I am wondering if there would be a problem if I changed my boot options to load that hard drive first and then access the files on the other hard drive, and would that prevent 12.04 from running since the other hard drive was loaded first?  

Let me know any suggestions.  Many thanks!!  :)

---

### Post by skyer2000 on 2012-07-13
I'm having the same issue, and unfortunately I am rarely around that computer.

---

### Post by OM55 on 2012-07-13
Likewise, I have a similar issue (although happens rarely) on all computer I have in remote locations (about 15 of them) . So it is obviously some bug in Vino and was there since Ubuntu 9.04. 
I think it may have to do with a specific code combination sent to the host that is not handled well and as a result the host Vino gets stuck. Since it is not running as other processes, you can not simply restart it. But there here are a couple of solutions:

1. You can always use NX Server & client. This is actually working faster and better especially when Internet communication is not too fast.
Let me know if you need help installing it, I'll send you step by step instructions.

However, with NX server the remote user gets his own copy of the desktop. So if you specifically need to show a remote person on the host desktop what you are doing, than VNC is the only way:

2. To restart the Vino server remotely, SSH into your remote computer and type/paste:

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
gconftool-2 --type bool --set /desktop/gnome/remote_access/prompt_enabled 0
export DISPLAY=:0.0
/usr/lib/vino/vino-server

```Alternatively you can prepare a script that you will be able to run via SSH every time the Vino server hangs. Just create a file (for example start-vino.sh) with the following code inside:

```
#!/bin/bash
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
gconftool-2 --type bool --set /desktop/gnome/remote_access/prompt_enabled 0
export DISPLAY=:0.0
/usr/lib/vino/vino-server

```then change its permissions to 744:
```
chmod 744 start-vino.ssh
```and the next time your Vino server crashes, log-in remotely via SSH:
```
ssh -l <your username> <ipaddress or domain name>

```and run the script, then try to VNC again.

Hope that helps!

---

### Post by skyer2000 on 2012-07-13
NX Server sounds like the best option, could you send the instructions?

---

### Post by OM55 on 2012-07-13
Here you go. In Ubuntu 12.04 host machine do the following:

_**On the host machine**_
```
    sudo add-apt-repository ppa:freenx-team/ppa  
    sudo apt-get update 
    sudo apt-get install freenx-server 

```This will install the free NX server on the host machine and it should be up and running in the background right away (notice that if you are using a previous version of Ubuntu the installation process is different.)

If the host machine is behind a firewall or NAT router, you will need to forward port 22 to the host machine.

**_On the remote machine_**
As for the NX client on the remote machine I recommend to install the free version of NX Client by NoMachine. It works very well. You can download it at:
[B][COLOR=Blue]
[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)[/COLOR][/B]

Just download and install the NX Free Edition for Linux (if you are using Windows, there is a Windows version as well).
To set up a connection profile you use the "NX Connection Wizard" (pretty self explanatory) and to connect you use the "NX Client for Linux" (or "...for Windows, if you are using Windows).

When you connect, the initial setting is "windowed", so your host virtual desktop will show in a "NX Client" window. If you click on the "Close" decoration button at the top of that window, you will be offered an option to "Terminate" or to "Disconnect".

"Terminate" - will leave all active processes running and will allow you to re-connect later on again to this active desktop.
"Disconnect" - it identical to "logoff" and will close all the process and desktop environment associated with your remote connection.

Although you can use the regular "Logoff" option from the Ubuntu system menu, I would advise to avoid doing that. The reason would be that the "Shut down" option is directly below, and if you accidentally shut down the host... you will have to have someone in person turning it on again.

Notice that every time you connect using NX Client you have the option to start a new virtual desktop environment with its own GUI and user processes, or you can re-connect to a previous environment that was not logged off.

If you start a new desktop, it will take a few seconds, similar to the regular logon process of Ubuntu. But if you reconnect to a previous desktop that were not logged off - the connection is very fast. So unless you have a reason why to logoff your virtual desktop every time, you can leave it running and simply connect and disconnect every time.

_**File transfer and remote printing**_
An added benefit to using NX Client is the ability to transfer files back and forth between the host and the remote as well as print from the host on your remote printer.
See the different configuration options in the NX Client (after setting up the connection). "Using NX Client for Linux", before connecting click on "Configure" and go to the "Services" tab. There you can define "Shares" and local printers that will show on your host desktop as network drives and network printers.

One last thing to remember: Unlike VNC, with NX the remote desktop you receive is an additional copy of the user desktop on the host. So if you have any programs or scripts starting automatically, the same will happen on the remote connection. So if you have any unique startup application that you can not have two copies run at the same time, you will need for example to create a different user on the system for remote access. There are ways for an application to know if it is running on a local machine or on the remote machine's virtual desktop, but this is beyond the scope of this reply...:)

That's it. Happy NXing!

---

### Post by skyer2000 on 2012-07-13
Looks like there might be a step missing, I'm to the point where I'm trying to login where it fails with: The NX service is not available or the NX access was disabled on host

Here is the log:

NX> 203 NXSSH running with pid: 7724
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 24.247.2.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

---

### Post by OM55 on 2012-07-13
Based on the log you provided it looks not like an installation issue but an authentication issue, meaning the username/password you provide for the log-in does not exist on the host system. Remember that it is case sensitive and ALL usernames are LOWER CASE. So if your username is "David" you should type in "david" in the username.

Another thing to look at would be the SSH key authentication. If you previously were able to connect to that computer using SSH, this may happen if the host computer has changed or its IP has changed. If you haven't been able to connect using SSH - that the cause of the problem.

So start step by step. 

1. First, to eliminate firewall issues, for the purpose of testing, put both host and remote on the same local network. This way you have no concern that the connection issue is because of a wrong firewall port setup.

2. Try to log in to the host using SSH. If you have the same username in the remote and the host, type in terminal:
```
ssh <IP or domain name>
```if it is a different username on the host, type:
```
ssh -l <your host username> <IP or domain name>
```If it is the first time an SSH connection is attempted to that IP or computer, you will first be asked if it is ok to save the IP and domain name in the "known hosts" local file (this is a security measure, in case someone changes the target computer or IP without letting you know - it wont allow connections to a different computer with same IP).

After a few seconds you should be prompted to type a password.

If that doesn't happen - you have a problem connecting via SSH and this is the underlying problem to solve first.

2. If all is fine, you will get the regular terminal prompt of your user on the host.
To confirm - you can type:
```
ls -l
```and verify that the file listing you see is the files in the home directory of the user at the host.

3. While you are at the host prompt, you can confirm that the freenx-server on the host is up and running. If the installation (described in my previous reply) went well, you should be able to see the file by:
```
ls -l /etc/init.d/freenx-server
```4. To check if the Free NX server is running type:
```
sudo /etc/init.d/freenx-server start
```If the server is already up and running, you would receive the response:
```
Not starting freenx-server, it's already started.
```If you receive a different response - the server was not running, so try _**again**_ right away to start it, if still no response, the server cannot start for some reason. Check the log files for clues.

5. Now that you have confirmed the server is running, and the SSH connection is working, you can disconnect the SSH connection by typing:
```
exit
```You will be back to your local terminal prompt.

6. Now try to connect with the NX Client. If the SSH connection was working and the server is running, the only reason the NX Client would not be able to connect is if the username and/or password are incorrect (remember - username is all lowercase).

7. The last step would be to make sure that on the router/firewall at the host (if any) port 22 is forwarded to the host machine's IP. Then reconnect your remote computer outside the firewall and try to connect. BUT see first the following note:

Note: If for the testing you connected your remote computer on the same local network as the host, and then connected again outside the firewall, from the point of view of the remote computer - the host's IP has changed! As a result the SSH connection will
Remember that every new SSH connection keeps the domain+IP pair of the host (together with a unique encryption key) in allowed_hosts file. If the host's IP or domain name change, SSH will not let you establish a connection any more - until you remove the old domain+IP from the known_hosts file. In fact, SSH will even issue a warning about an "offending IP".

Solutions - 
a. Try first the connection using NX client. It will automatically ask you to accept the new IP+domain+key and that's it.

b. You can instruct SSH to remove the IP+domain record by typing:
```
sudo ssh-keygen -R <domain-name>
sudo ssh-keygen -R <ip-address>

```Notice that although the IP and domain were added both at the same time, you have to remove each one separately issuing two separate commands.

c. You can edit the known_hosts file (located under the '.ssh' directory in your home directory on the remote) to remove this entry. But if you are not sure what you are doing I strongly recommend not to do that.

That's about it. If you follow the 'logical chart' steps above you should be up and running.
If it still doesn't work, post here what you did step-by-step and what responses you received and I'll try to help further.

---

