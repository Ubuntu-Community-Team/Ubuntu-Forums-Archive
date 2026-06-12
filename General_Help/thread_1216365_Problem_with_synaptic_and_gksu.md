---
title: "Problem with synaptic and gksu"
date: 2009-07-18
forum: General Help
---

### Post by mrlizard123 on 2009-07-18
I'm running Jaunty and I'm not sure why but I am having this strange problem:

When update manager pops up to update some packages, or when I run synaptic from the System->administration->synaptic.. I get these errors:

"Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Cannot initiate the connection to 192:8080 (0.0.0.192). - connect (22 Invalid argument)"

(many of them)

When I do "reload package information" for example. It says it is trying to download 48 files...

However, if I open synaptic from the terminal with either sudo or as root it only downloads 24 files and I get no errors.

I have replaced my old sources.list with the installation default but this did not make any difference and am mightily confused! Before reverting to the default sources.list the number of files it said it was downloading seemed very high, hard to tell now I've blown the old sources file away but I guess it must have been double or thereabouts.

Same as above applies to running update-manager too.

Can anyone give me a nudge in the right direction??

Many thanks in advance :)

---

### Post by mrlizard123 on 2009-07-19
Has no one experienced this issue or have any suggestions where to start looking?

---

### Post by michy99 on 2009-07-19
Do you get any error messages if you run this?```
sudo apt-get update
```

---

### Post by mrlizard123 on 2009-07-21
> **michy99 said:**
> Do you get any error messages if you run this?```
sudo apt-get update
```

Nope, but if I do gksu apt-get update instead I do, same errors:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  Cannot initiate the connection to 192:8080 (0.0.0.192). - connect (22 Invalid argument)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  Cannot initiate the connection to 192:8080 (0.0.0.192). - connect (22 Invalid argument)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Another thing to note - when installing/updating any software using sudo instead of gksu it says that the software is unauthenticated for anything and everything - all coming from the ubuntu standard repositories

---

### Post by mrlizard123 on 2009-11-07
Has anyone got any suggestions on how to fix this? I've basically put up with it for ages but am finding myself getting more than a little peeved with it now...

sudo apt-get ....
sudo update-manager ....
etc
all work

gksu apt-get ....
etc
all give me an error with "Cannot initiate the connection to 192:8080 (0.0.0.192). - connect (22 Invalid argument)"

I've googled and searched but not come across anything that seems even able to point me in the right direction.

---

### Post by Lekensteyn on 2009-11-07
192:8080 seems to be a part of a local IP address: 192.168.x.x:8080.
Just notices this, I'm not sure what this has to do with the error.

What do you get if you enter:
```
kdesudo apt-get update
```

---

### Post by mrlizard123 on 2009-11-07
> **Lekensteyn said:**
> 192:8080 seems to be a part of a local IP address: 192.168.x.x:8080.
Just notices this, I'm not sure what this has to do with the error.

What do you get if you enter:
```
kdesudo apt-get update
```

I can see that it's trying to resolve some nonsense but I don't know where it's coming from :(

I'm running gnome and don't have kdesudo, I'm assuming gksu is the equivalent in gnome which is where the problem lies, seems that this is the mechanism used for all applications in the menus etc since they are not being run at terminal and need a popup for the password to authenticate.

---

### Post by mrlizard123 on 2009-11-08
Just finished upgrade to Karmic Koala and still having the same issues... disappointed to think that the only solution may be to completely remove ubuntu and start over.

---

### Post by mrlizard123 on 2009-12-07
> **mrlizard123 said:**
> Just finished upgrade to Karmic Koala and still having the same issues... disappointed to think that the only solution may be to completely remove ubuntu and start over.

I ended up reinstalling from scratch to resolve this - not the most favourable solution by a long chalk but it has been resolved at least...

---

### Post by yazid on 2009-12-07
Hi,
I have the same problem, just instead of the error code 22 i have the following:

W: Failed to fetch [http://mirrors.xmission.com/ubuntu/dists/intrepid/Release.gpg](http://mirrors.xmission.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to 217.70.56.161:8080 (217.70.56.161). - connect (111 Connection refused)

W: Failed to fetch [http://mirrors.xmission.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://mirrors.xmission.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to 217.70.56.161:8080 (217.70.56.161). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.


And it's not acceptable to end up installing from scratch, we have to find a solution!!

---

### Post by mrlizard123 on 2009-12-08
Are you sure it's the same problem? It works with sudo but not via menus/gksu? Or does it not work at all?

It looks like you're connecting on 8080 and getting a connection refused message.

Try going into System->Administration->Software Sources then see what repositories you have and maybe uncheck them until only using the main ubuntu repos.

Have you done anything with configuring proxies? Either for apt specifically or generally?

Do you get any output if you issue ```
echo $http_proxy
``` in a terminal?

Do you have an /etc/apt/apt.conf file? and if so - cat its contents and have a look at what's in there...

That's all I can think of off the top of my head, let me know how you get on :)

---

