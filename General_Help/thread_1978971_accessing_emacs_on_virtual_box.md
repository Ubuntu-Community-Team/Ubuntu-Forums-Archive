---
title: "accessing emacs on virtual box"
date: 2012-05-12
forum: General Help
---

### Post by batb on 2012-05-12
I am accessing a virtual box through ssh -p, and it all works fine. but when I try the following command, I don't see the emacs window open. How do I access the emacs window when logged into the virtual box

```
ba@ubuntu-VB:~$ emacs &
[1] 6564
ba@ubuntu-VB:~$ 
```

---

### Post by codemaniac on 2012-05-12
"emacs &" launches Emacs from an xterm. The ampersand puts Emacs into the background. As X provides the display for Emacs, this setup is fine.

In an SSH connection to a remote server you are not having an X environment .
But if you have SSH set up to forward X, you can run Emacs (and other X applications) remotely.

---

### Post by batb on 2012-05-12
> **codemaniac said:**
> "emacs &" launches Emacs from an xterm. The ampersand puts Emacs into the background. As X provides the display for Emacs, this setup is fine.

In an SSH connection to a remote server you are not having an X environment .
But if you have SSH set up to forward X, you can run Emacs (and other X applications) remotely.

@codemaniac, I don't understand the reference to the X environment. Can you please clarify. thanks.

EDIT: would you be referring to XWindows. If so, can you let me know if it is installed automatically or do I have to install it. And will that interfere with Gnome. Also, how would one go about configuring SSH to forward X.[COLOR=#1f497d][FONT=&quot][/FONT][/COLOR]

---

### Post by sudodus on 2012-05-12
Try
```
ssh -X
``` or ```
ssh -Y
``` to manage GUI applications via ssh. Read the manual pages about it: In a public network it is risky to use X11 forwarding for security reasons.

---

### Post by batb on 2012-05-12
> **sudodus said:**
> Try
```
ssh -X
``` or ```
ssh -Y
``` to manage GUI applications via ssh. Read the manual pages about it: In a public network it is risky to use X11 forwarding for security reasons.

@sudodus, thanks. follow-up questions
1. on the security risk - can you elaborate a little more on that. also, is disabling access the only way to defend against it.
2. how does one restrict access to select remote machines so anything not explicitly permitted is prohibited.
3. if the machine accessing remotely doesn't have a fixed IP address, how can it be authenticated when a connection attempt is made
[COLOR=#1f497d][FONT=&quot][/FONT][/COLOR]

---

### Post by sudodus on 2012-05-12
> **batb said:**
> @sudodus, thanks. follow-up questions
1. on the security risk - can you elaborate a little more on that. also, is disabling access the only way to defend against it.
2. how does one restrict access to select remote machines so anything not explicitly permitted is prohibited.
3. if the machine accessing remotely doesn't have a fixed IP address, how can it be authenticated when a connection attempt is made
[COLOR=#1f497d][FONT=&quot][/FONT][/COLOR]
1. Are you running in a private LAN at home or in a LAN of a company or university or ...
From [FONT="Courier New"]man ssh[/FONT]
```
     -X      Enables X11 forwarding.  This can also be specified on a per-host
             basis in a configuration file.

             X11 forwarding should be enabled with caution.  Users with the
             ability to bypass file permissions on the remote host (for the
             user's X authorization database) can access the local X11 display
             through the forwarded connection.  An attacker may then be able
             to perform activities such as keystroke monitoring.

             For this reason, X11 forwarding is subjected to X11 SECURITY
             extension restrictions by default.  Please refer to the ssh -Y
             option and the ForwardX11Trusted directive in ssh_config(5) for
             more information.

     -x      Disables X11 forwarding.

     -Y      Enables trusted X11 forwarding.  Trusted X11 forwardings are not
             subjected to the X11 SECURITY extension controls.

``` so it is only a risk if you are in a LAN where others have administrative privileges. But you can run emacs in text mode (the old way) via ssh
```
emacs -nw
``` In my system (Ubuntu 10.04 LTS) emacs defaults to text mode, if X11 forwarding is not enabled even without -nw.

I don't know the details about the X11 SECURITY extension controls and how efficient it is.

> 2. how does one restrict access to select remote machines so anything not explicitly permitted is prohibited.
Are you asking as an administrator or a user? I think the administrator is responsible and should lock out users, and this is outside my knowledge.

> 3. if the machine accessing remotely doesn't have a fixed IP address, how can it be authenticated when a connection attempt is made

It is easy if you log in with a password, but not as secure as if the system uses host-based authentication or public key authentication. Public key authentication should work independent of the ip address.

---

### Post by batb on 2012-05-12
> **sudodus said:**
> 1. Are you running in a private LAN at home or in a LAN of a company or university or ...
From [FONT=Courier New]man ssh[/FONT]
```
     -X      Enables X11 forwarding.  This can also be specified on a per-host
             basis in a configuration file.

             X11 forwarding should be enabled with caution.  Users with the
             ability to bypass file permissions on the remote host (for the
             user's X authorization database) can access the local X11 display
             through the forwarded connection.  An attacker may then be able
             to perform activities such as keystroke monitoring.

             For this reason, X11 forwarding is subjected to X11 SECURITY
             extension restrictions by default.  Please refer to the ssh -Y
             option and the ForwardX11Trusted directive in ssh_config(5) for
             more information.

     -x      Disables X11 forwarding.

     -Y      Enables trusted X11 forwarding.  Trusted X11 forwardings are not
             subjected to the X11 SECURITY extension controls.

``` so it is only a risk if you are in a LAN where others have administrative privileges. But you can run emacs in text mode (the old way) via ssh
```
emacs -nw
``` In my system (Ubuntu 10.04 LTS) emacs defaults to text mode, if X11 forwarding is not enabled even without -nw.

I don't know the details about the X11 SECURITY extension controls and how efficient it is.


Are you asking as an administrator or a user? I think the administrator is responsible and should lock out users, and this is outside my knowledge.



It is easy if you log in with a password, but not as secure as if the system uses host-based authentication or public key authentication. Public key authentication should work independent of the ip address.

running a private LAN at a home.
I was asking as an administrator

---

### Post by codemaniac on 2012-05-12
> **batb said:**
> @codemaniac, I don't understand the reference to the X environment. Can you please clarify. thanks.

EDIT: would you be referring to XWindows. If so, can you let me know if it is installed automatically or do I have to install it. And will that interfere with Gnome. Also, how would one go about configuring SSH to forward X.[COLOR=#1f497d][FONT=&quot][/FONT][/COLOR]

hello batb , forgive my words for being cryptic.
All you can do , while being on a ssh session , you can fireup emacs in foregroung instead of background .it will open up in terminal and will let you edit files .

---

### Post by batb on 2012-05-13
> **codemaniac said:**
> hello batb , forgive my words for being cryptic.
All you can do , while being on a ssh session , you can fireup emacs in foregroung instead of background .it will open up in terminal and will let you edit files .
hello codemaniac,
so basically edit using emacs -nw as sudodus also mentioned.
or i could also just go emacs <filename>. I tried that, the challenge is: I have to know the shortcut keys to save, or close the file, search for strings etc., because it doesn't let me use the menus. There should be a way to use the menu as one would in an emacs window opened with emacs&. Isn't that right?

---

### Post by codemaniac on 2012-05-13
Emcas is best when it is on terminal .If you have forwarding problem in X while being on ssh it is the only option .

---

### Post by sudodus on 2012-05-13
> **batb said:**
> running a private LAN at a home.
I was asking as an administrator
At home you need not worry, so use

```
ssh -X
``` or ```
ssh -Y
``` which should give you a access to gui applications (emacs will be i gui mode in its own window with the menus). It works for me. Does it work for you?

---

### Post by sudodus on 2012-05-13
The attached file will show how to do and what it can look like, when you use [FONT="Courier New"][SIZE="3"]ssh -X ...[/SIZE][/FONT]

---

### Post by batb on 2012-05-13
> **sudodus said:**
> The attached file will show how to do and what it can look like, when you use [FONT=Courier New][SIZE=3]ssh -X ...[/SIZE][/FONT]
thanks for the attachment. I figured out the problem - it is with ssh -X.
when I just type ssh-X, I get the following:
```
ssh -X
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
```

so I did:
```
ssh -X host@xx.xx.xxx.xx1
ssh: connect to host xx.xx.xxx.xx1 port 22: Connection refused
```

how do I get that problem resolved..I am logging in from a different network than the host server

---

### Post by sudodus on 2012-05-13
> **batb said:**
> thanks for the attachment. I figured out the problem - it is with ssh -X.
when I just type ssh-X, I get the following:
```
ssh -X
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
```

so I did:
```
ssh -X host@xx.xx.xxx.xx1
ssh: connect to host xx.xx.xxx.xx1 port 22: Connection refused
```

how do I get that problem resolved..I am logging in from a different network than the host server

In your first post you wrote that you used ssh -p

```
     -p port
             Port to connect to on the remote host.  This can be specified on
             a per-host basis in the configuration file.

```
which means that you specify a port (other than the default #22). You need to do so now too.

---

### Post by batb on 2012-05-13
> **sudodus said:**
> In your first post you wrote that you used ssh -p

```
     -p port
             Port to connect to on the remote host.  This can be specified on
             a per-host basis in the configuration file.

```which means that you specify a port (other than the default #22). You need to do so now too.

ok, I connect into the remote computer using ```
ssh -p.....
```and it works. now after I am logged in to the remote host, I try ```
ssh -X
```so that I can access emacs via emacs &
isn't that what I was supposed to do :-(

am I supposed to set $DISPLAY var....I did some google searches and there seems to be mention of 
```
export DISPLAY=":0.0"
```

I ran that but it did not change anything for me...

---

### Post by sudodus on 2012-05-14
> **batb said:**
> ok, I connect into the remote computer using ```
ssh -p.....
```and it works. now after I am logged in to the remote host, I try ```
ssh -X
```so that I can access emacs via emacs &
isn't that what I was supposed to do :-(

am I supposed to set $DISPLAY var....I did some google searches and there seems to be mention of 
```
export DISPLAY=":0.0"
```

I ran that but it did not change anything for me...
You need both options -X and -p at the same time

```
ssh -X -p port username@hostname
```

where port is your actual port number, username & hostname are the actual names to log into the ssh server.

Usually the display will be set correctly automatically.

---

