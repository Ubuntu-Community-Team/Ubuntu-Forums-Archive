---
title: "StartUp Manager tools"
date: 2010-06-05
forum: General Help
---

### Post by rizameister on 2010-06-05
I have installed newest StartUp Manager on Ubuntu, but I can't access all the options. How to got them all?
[IMG]https://help.ubuntu.com/community/StartUpManager?action=AttachFile&do=get&target=sum.png[/IMG][IMG]https://help.ubuntu.com/community/StartUpManager?action=AttachFile&do=get&target=sum-appearance.png[/IMG]

For example, I can't change appearance, don't have this tab, just a few boot options like resolution, color depth etc.

---

### Post by XSAlliN on 2010-06-05
You can't for now, since there is no specific support for Lucid regarding those options. And don't see any update in that direction...

[http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

[https://launchpad.net/startup-manager/](https://launchpad.net/startup-manager/)

> Jimmy Rönnholm  said on 2009-04-12:

The thing is, some options didn't work even with earlier versions of Ubuntu... since SM was originally intended for Debian and Debiand doesn't release new versions as often as Ubuntu. Which to some differences, and therefore the author had to made a "specific version of SM  for a specific version of Ubuntu". The author did give an answer in this direction (more specifically for Ubuntu 9.04) where similar problems have been reported:

Yes, I am aware of these problems, and it is a small dilemma.
You see, when I wrote this program Ubuntu and Debian worked pretty much the same when it comes to editing menu.lst.
It was preferred to edit those commented out lines, such as '# defoptions=splash vga=795' and then running update-grub, which would overwrite everything in the section that begins with '### BEGIN AUTOMAGIC KERNELS LIST' and apply values from those comments.

Now, a lot of users had hand edited the entries in the automagically generated list so when update-grub was run(for example at a kernel update) their customizations were overwritten. Therefore Ubuntu devs changed the way update-grub works and the behavior startup-manager depended on. I dont know exactly how update-grub works now, but I think it still works the way sum expects it to when menu.lst has never been hand-edited.

Further, as I understand, we are not supposed to use the vga=xyz on the kernel line anymore in Ubuntu. Resolution for the boot splash is changed in /etc/usplash.conf. On Debian with splashy as the bootsplash, the vga=xyz line is still the way to set splash resolution though.

So, since Ubuntu has changed a lot during the last few releases, I would have to change a lot in startup-manager to adapt to this and probably make it an Ubuntu-only tool.
I have considered doing this, but then we will probably have kernel modesetting and plymouth in Ubuntu Karmic. Grub2 should not be too far away either, with its new update-grub system.

Therefore, I am tempted to hold off doing these changes and see what happens with Plymouth and Grub2.
If they get more widespread use, and distributions dont differ too much in their configuration, I would rather target Plymouth and Grub2 only and hopefully have the tool usable on more distros.

So that is the options I see:
*Keep it broken for recent Ubuntu versions but working with Debian.
*Rewrite its behavior to make it compatible with recent Ubuntu versions but incompatible with Debian and older Ubuntu versions, and at the same time duplicating most of what tools like kgrubeditor can already do.
*Keep it broken with recent Ubuntu versions for now, but rewrite when and if Plymouth and Grub2 get more widespread use so it is usable on more distros rather than less.

Currently I am leaning towards the third option, and am recommending kgrubeditor as a replacement in the meantime.

I hope that answers why things are broken right now.

...

On the bright side: **the important options work** (guess that's why it's still available)... ;)

---

