---
title: "Ubuntu in High-school"
date: 2009-07-14
forum: General Help
---

### Post by bogdan_5844 on 2009-07-14
So,I finally managed to get my high school's IT manager to install Ubuntu on our High-School (the network was full of viruses)
The computers we use in our 3 programming labs are from 2001,but they run Ubuntu perfectly.

And now comes the problem...

Here,in Romania,the idiots at government want us to learn the "ub3r-k001"(not) Microshit Office 2007. (everyone hates it!)

I was thinking of making all of the computers the students use thin-client terminals,and to make a server with a main Ubuntu installation (a more powerful computer) which will have Office 2007 installed (trough WINE) and all other applications that the students use (most Edubuntu applications)

Can somebody help me with a tutorial or instructions in setting this up? :p I've been using Ubuntu for 2 years,but I don't really know how to manage the server/thin client part of the job

Thanks,you Rock!:guitar:

---

### Post by scouser73 on 2009-07-14
Well done for getting your school's IT department to switch to Ubuntu.

---

### Post by bogdan_5844 on 2009-07-14
Yes,I got that :D the geography,biology etc. labs already have Ubuntu on their teacher's computers.

But I have no idea on how to set up the IT laboratory...can you help me?:(

---

### Post by CatKiller on 2009-07-14
Congratulations on getting the school to make the switch.

> **bogdan_5844 said:**
>  I was thinking of making all of the computers the students use thin-client terminals,and to make a server with a main Ubuntu installation (a more powerful computer) which will have Office 2007 installed (trough WINE) and all other applications that the students use (most Edubuntu applications)

I suspect that that kind of solution is against the terms of the Office EULA. Whether those terms are enforceable in your country isn't something that I'm qualified to speculate on.

I don't know how well Office 2007 works in Wine. It might be better to run it in a virtualised environment if it doesn't work in Wine. But again you run into licensing problems, and you may well take a performance hit too.

If it does work in Wine, you can always symlink each user's .wine directory (which holds the pretend C: drive) to some centralised location. This location could be a remote machine mounted with NFS. /etc/skel is the location of the template for a new user's Home directory, so you'd probably want to look at configuring that in the environment that you deploy so that you don't have to do it for every user manually. /usr/share/applications is the location for the system-wide launchers, and you'll probably want to create a .desktop file there so that each user gets a menu entry to run Office.

If you're going to have access to Wine on each machine, you'll probably need to lock it down in some fashion so that the users aren't spending all their time installing Windows games. Crossover may have some ability to do this, but I've never used it so I couldn't say. You'll probably find it useful to mount the pretend C: drive read-only so that the user can't install stuff there, and give them a different (per-user) location as another pretend drive to save their documents.

Depending on how far you want to go into the whole thin-client approach there's quite a lot that you can do. It's possible to make a machine boot entirely from the network, or you could just have some locations (/boot, /bin, /usr, say) mounted from a remote machine with the rest stored locally. It's the kind of thing that's been done for decades with UNIX-like machines, so I'd imagine there are quite a few resources out there outlining different approaches you could take.

Good luck!

---

### Post by t4thfavor on 2009-07-14
Thin clients are pretty easy, there is the LTSP project. All I did to have a working install is follow this howto [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

It makes it drop dead simple. As for the office thing, I stopped even trying to run Microsoft software, so I really can't be of any help.

---

### Post by bogdan_5844 on 2009-07-14
Thanks for the advice,guys :D

CatKiller,I know this has been possible for ages,that's just one of the many,many reasons I wanted Ubuntu or another Linux on our high school IT departments.

I shall try to look at those folders...I haven't really understand how to set them up,but I get the big picture (excepting the part with networked boot folders...That sounds very interesting,it seems to be exactly what I'd want to do)
If the system would be installed on another computer,then the hard drive of the user's computer could be used for storing files,right?;)
And,I was thinking if there is a way to install at the same time (with the same configuration) on all the computers in the network,eventually without cd-rom (many of them have the cd-r units broken,usb is good tough)
Maybe some of you guys can help me with this :D 

P.S.: Regarding the Office license,I do think that in Romania,software restrictions in high-schools and such are not that restrictive.I say this because I've seen many schools using the same implementation,or a very similar one.(Linux+Micro$haft combo)

---

### Post by CatKiller on 2009-07-14
> **bogdan_5844 said:**
>  If the system would be installed on another computer,then the hard drive of the user's computer could be used for storing files,right?;)

Personally, I wouldn't. What if the user wants to use a different computer, or the one they have been using breaks and needs to be replaced? Storing personal documents on a networked location means that they can be backed up along with everything else as part of the normal IT department maintenance, and that they can be accessed from any machine. Tying these locations to a particular user ID is necessary so that each user can only access their own documents and not those of other users.

Another option is to require each user to have their own thumb drive for document storage so that they and they alone are responsible for their safekeeping. This does give another vector for unauthorised software getting onto the network, though.

Either way, you'll need to find some way to configure that location to be available to Wine so that they have somewhere to save the documents they create in Office.

> And,I was thinking if there is a way to install at the same time (with the same configuration) on all the computers in the network,eventually without cd-rom (many of them have the cd-r units broken,usb is good tough)

This is generally a solved problem for any OS. Corporate deployments generally require that the same image be used for thousands of machines, since no one wants to have to go through the pain of installing and configuring that many multi-user machines by hand. I believe it's one of the "Enterprise" tools for Windows that is able to push images out over the network. For Linux you'd probably use UNetbootin or Remastersys to create and deploy your images.

This is the kind of thing that people generally train for. If you're going to work out how to do it all yourself from scratch it will take quite a lot of research first. In case you were wondering why people pay for support contracts even with Free software, it's for this kind of thing :)

---

### Post by bogdan_5844 on 2009-07-14
From what I understand,(correct me please if I am wrong) I should set up an Linux Thin Client server on the network,set some forwarding on the main router/switch,and then set every thin client to boot from network (e.g. boot from the main server's image)and then the thin clients' would download an initfs image (or something like that)that contains the system.

I was thinking about saving the files on the hard drive because of the ECDL program (I don't know if you heard about it,it's kinda like a "computer driving license",a dumb thing actually) which needs,on the module exam,each participant to have it's own folder to make modifications in.Although this could be solved if I make folders on the desktop with each user's name.

Anyway,I am willing to invest time in researching,trying,learning how to do this.I don't really have the option to invest money in training,so that's why I want to learn by myself.

The thumbdrive option fails from the start,many students forget to bring their manuals at school,what can I say more about thumbdrives ):P

If I get to a remote system "image" that should be the copy that each thin client downloads,I think that I can get my way trough that.The problem is getting at that :p

---

### Post by lensman3 on 2009-11-13
This is a quote from another thread and then I had to look for your thread.  This might be your solution.  Sorry I don't have the exact thread number.  The thread had to do with encrypting a small notebook HD and the fact there was slow response because the files had to be un-encrypted.

A QUOTE from somebody::::>
ah, yes... a regular HDD. That probably makes a huge difference. You could try mounting unionfs your .mozilla directory to tmpfs. If you want to keep anything just write a script that runs on shutdown that syncs the "real" .mozilla directory w/ the tmpfs one. When initially reading it will be slow, but subsequent reads will be blazing fast.

---

