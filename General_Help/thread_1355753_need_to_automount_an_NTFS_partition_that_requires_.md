---
title: "need to automount an NTFS partition that requires a password at system startup"
date: 2009-12-15
forum: General Help
---

### Post by flak_monkey on 2009-12-15
I've looked through the forums and have not found anything specific to my case. I've got xp64 on the other side of this computer and a second hard drive that's just got all of my data, music, pictures, bittorrents, video on it. When I click on it in "places" it asks for my password. I would like it auto mounted when I log in to Ubuntu. How do I accomplish this? 
I know that you'll need some info from me on the way my drives are configured, what do I type in the terminal to help you see that? 

Thanks

---

### Post by sisco311 on 2009-12-15
> **flak_monkey said:**
> 
I know that you'll need some info from me on the way my drives are configured, what do I type in the terminal to help you see that? 

Thanks

Nope, we don't need any future info. :)

You can use [ntfs-config]("apt://ntfs-config") (click the link to install it) a GUI utility to easily configure all of your NTFS devices. 

See:
[http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

---

### Post by Swagman on 2009-12-15
> **sisco311 said:**
> Nope, we don't need any future info. :)

You can use [ntfs-config]("apt://ntfs-config") (click the link to install it) a GUI utility to easily configure all of your NTFS devices. 

See:
[http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

Actually, clicking on your link **DOESN'T** install it
[img]http://www.upload3r.com/serve/151209/1260889679.jpeg[/img]

And my pet fave peeve about Linux in general.....

 [img]http://www.upload3r.com/serve/151209/1260889746.jpeg[/img]

So I wonder where the heck*** THAT*** application lives ?

That "opens with" issue really needs sorting out.  The file calling for it knows ( or should) what it needs to run so why aren't the programs that can run it not listed ?

---

### Post by sisco311 on 2009-12-15
> **Swagman said:**
> 
That "opens with" issue really needs sorting out.  The file calling for it knows ( or should) what it needs to run so why aren't the programs that can run it not listed ?

It's listed. It's an apturl link, you have to open it with apturl (See the link in my signature for details). Highlight apturl, select the *Remember my ....* check box and click OK.

But you can install it via Add/Remove (or Ubuntu Software Center) or Synaptic Package Manager as well.

Check out the link from my first post.

---

### Post by flak_monkey on 2009-12-15
Thanks mate, this worked fabulously for me. Cheers!

For what it's worth, I use opera so I opened his link in firefox and it worked fine for me. It did ask me what to do with the file, and suggested gdeb package installer, IIRC, so I went with that.

---

