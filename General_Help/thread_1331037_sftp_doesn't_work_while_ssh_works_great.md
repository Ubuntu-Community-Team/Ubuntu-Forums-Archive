---
title: "sftp doesn't work while ssh works great"
date: 2009-11-18
forum: General Help
---

### Post by korihor on 2009-11-18
Hi all,

I installed openssh-server on one of my ubuntu boxes, and I can now ssh in.
However, I can't sftp in! That's never happened to me before. I tried running sshd in non-daemon mode, and this is what I got from it:

subsystem request for sftp
debug1: subsystem: exec() /usr/lib/openssh/sftp-server
debug1: Received SIGCHLD.
debug1: session_by_pid: pid 28192
debug1: session_exit_message: session 0 channel 0 pid 28192
debug1: session_exit_message: release channel 0
debug1: session_by_channel: session 0 channel 0
debug1: session_close_by_channel: channel 0 child 0
debug1: session_close: session 0 pid 0
debug1: channel 0: free: server-session, nchannels 1
Connection closed by 10.0.1.12
debug1: do_cleanup
Transferred: sent 1960, received 1424 bytes
Closing connection to 10.0.1.12 port 46314
debug1: PAM: cleanup
debug1: PAM: deleting credentials
debug1: PAM: closing session

On the client end, nautilus just says "Could not open location 'sftp://..." "ssh program unexpectedly exited".

Googling around led to the suggestions the the permissions might be wrong on /dev/null (mine are ugo+rw which I think is fine), and setting uncommenting "PasswordAuthentication yes" in sshd.conf which didn't work.

Anyone know what the problem is?

Thanks in advance and for helping the community!

---

### Post by lavinog on 2009-11-19
how are you trying to connect (nautilus or command line)
are you using the standard port 22?

---

### Post by korihor on 2009-11-19
Hi lavinog, thanks for your help.

Yes I am using standard 22.
For ssh shell access and scp I am using the command line. That works fine.

For sftp I have tried Nautilus and FileZilla, both fail with their own generic messages, and both failures cause the same ssh server error I pasted in my first post.

I tried putting openssh-server on my other machine, and I replicated the error there too. (Firewall is down). I'm not sure how I botched this, I've installed ssh many times without trouble using just:

sudo apt-get install openssh-server
sudo /etc/init.d/ssh start

Any help would be appreciated.

---

### Post by lavinog on 2009-11-19
what happens when you try using sftp from the command line?

also have you tried using ssh with nautilus:
in the address bar instead of sftp://host  try ssh://host

---

### Post by korihor on 2009-11-19
Hi,

I ran ssh://host in Nautilus, it gives the same error that sftp://host does (listed in my first post).

I tried sftp on the command line using sftp -v, after entering my password here is the result:

debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending subsystem: sftp
debug1: client_input_channel_req: channel 0 rtype exit-signal reply 0
debug1: client_input_channel_req: channel 0 rtype [email]eow@openssh.com[/email] reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
Transferred: sent 1424, received 1960 bytes, in 0.4 seconds
Bytes per second: sent 3279.5, received 4513.9
debug1: Exit status -1
Connection closed

Thanks again for your help.

---

### Post by lavinog on 2009-11-19
did you manipulate the ssh config files in /etc/ssh?
Have you checked for updates?
apt-get might hold back updates to openssh, but aptitude shouldn't.
Is this a karmic or jaunty server?

---

### Post by korihor on 2009-11-19
Hi again,

Both machines are Karmic desktops, one i386 one amd64.

I have not touched the configuration files, other than to try uncommenting the password authorization line on one computer, which I re-commented after it failed.

My version is "Version: 1:5.1p1-6ubuntu2", I can't interpret most of the rest of the output of "aptitude show openssh-server", but these lines may be of interest:

Recommends: xauth
Suggests: ssh-askpass, rssh, molly-guard, openssh-blacklist,
          openssh-blacklist-extra, ufw
Conflicts: rsh-client (< 0.16.1-1), sftp, ssh (< 1:3.8.1p1-9), ssh-krb5 (<
           1:4.3p2-7), ssh-nonfree (< 2), ssh-socks, ssh2

I am currently reinstalling ubuntu on one of my machines (unrelated reasons), so I will try "aptitude install" on that one and see if the problem persists.

Thanks for your help. (And sorry for not formatting my posts, I'll look through the forum syntax later, time for bed!)

---

### Post by korihor on 2009-11-19
oh, and yes I have checked for updates. none are available.

---

### Post by lavinog on 2009-11-19
All of my servers are still running jaunty at the moment so I am not familiar of any changes in karmics configuration yet.
I am out of ideas...maybe the reinstall will help.

---

### Post by korihor on 2009-11-19
okay thanks so much anyway, i really appreciate it.

I will report back if a clean install of karmic and openssh-server replicates the problem. If so, a bug report is in order, but I have an almost impossible time believing a service as popular as ssh could be broken in karmic without everyone on the planet knowing about it :)

---

### Post by korihor on 2009-11-19
Reinstalled on my netbook. SFTP works fine. All I did was update ubuntu, install openssh-server, and test.
So as for why it was broken on my netbook and my desktop . . . I guess some package I installed on both broke it? Or something like that? I'll test periodically to try and isolate the incompatible preference/behavior/action. Maybe it will be useful to someone.

---

### Post by korihor on 2009-11-19
Problem replicated on the clean install!

All I did was install my normal packages using apt-get (about 20 of them).
I'll go package by package tomorrow and submit a bug report.

Okay that's enough of my monologue. Thanks for your help and have a good night.

---

### Post by Krzysztow on 2011-01-13
Hi. I have some input, whereas I don't know if it holds to Your problem. Moreover I see, the post is already one year old, but it's the one that shows up as a first in google and can help some other people. 

I was logging to sftp server using Nautilus and all worked fine, unless I generated file with public keys in ~/.ssh/id_rsa. The key there was set with passphrase and after that Nautilus stopped working (connecting to server). Deleting this file helped again. I don't know how to go around the paassphrase (mine was set to blank), but maybe it helps somehow.

Greetings,
Chris.

---

### Post by nathan.f77 on 2011-09-20
Hi, sorry to resurrect an old thread. I also had the problem, but found the solution on this blog post: [http://websaucesoftware.com/ubuntu/ssh-works-sftp-doesnt-on-ubuntu-10-04](http://websaucesoftware.com/ubuntu/ssh-works-sftp-doesnt-on-ubuntu-10-04)

It references the [OpenSSH FAQ]("http://www.openssh.org/faq.html#2.9"), which states:

> [INDENT]2.9 – sftp/scp fails at connection, but ssh is OK.
 sftp and/or scp may fail at connection time if you have shell  initialization (.profile, .bashrc, .cshrc, etc) which produces output  for non-interactive sessions. This output confuses the sftp/scp client.  You can verify if your shell is doing this by executing:
     ssh yourhost /usr/bin/true
 If the above command produces any output, then you need to modify your shell initialization. 
 [/INDENT]

This solved it for me. I had 'bind' statements in my .bash_rc that produced this error: > .bashrc: line 249: bind: warning: line editing not enabled

Solved by detecting the presence of a terminal:

```

case "$TERM" in
xterm*|rxvt*)
    bind "\"\C- \":  \"git_prompt 'git commit -a'\n\""
    bind "\"\C-x \": \"git_prompt 'git commit'\n\""
    ;;
esac
```

---

