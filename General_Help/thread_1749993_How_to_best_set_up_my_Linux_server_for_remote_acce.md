---
title: "How to best set up my Linux server for remote access"
date: 2011-05-05
forum: General Help
---

### Post by Bioinfoswede on 2011-05-05
Hi all!

First post here, pretty much a newbie to Ubuntu. I have a question about how to set up my server for remote access, but first some general info.

I work as a bioinformatician at a university and we recently bought a server with a lot of internal memory to use for our analyses. Ubuntu server 64bit is installed, and I also added the graphical interface as I still find it easier to do some things through "pointing and clicking".

The server is rack mounted and will generally not be physically available to me, at least not easily, and I will usually work with it remotely from my MacOSX computer. Most of the things I need to do can be done by simply SSHing to it through a terminal on my Mac, but sometimes I have found it useful to use the graphical interface, for example when adding more users or to use the synaptic package manager. To be able to do this remotely I started the remote desktop service and it works fine with a VNC client on my Mac.

The problems start when I need to restart the server. It seems I need to be physically present at the server and login there to get a desktop which I can connect to with my VNC client. As the server will not be availble to me easily, this is a problem.

How would you suggest I set up the server to do what I need? It would be great if I could do everything remotely, including restarting the server and still be able to use the remote desktop. Or should I skip the remote desktop and perhaps rely on X11 to get some graphical capabilities? Can I access the Synaptic Package manager without the remote desktop?

Any suggestions how I should do this, including just simple terms to search for or links would be great. I have done quite  a lot of searches myself, but have so far not found what I am looking for. With more experience I can see how I would drift more towards doing everything via SSH, but right now the option of a graphical interface would be great to have.

---

