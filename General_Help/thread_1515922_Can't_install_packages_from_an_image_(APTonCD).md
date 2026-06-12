---
title: "Can't install packages from an image (APTonCD)"
date: 2010-06-23
forum: General Help
---

### Post by duddy67 on 2010-06-23
Hi,

Well, I think all is in the title.
I created an image disk of my installed packages with APTonCD, 
then I burned a CD in order to install these packages on my 
not internet connected PC.
I typed: ***sudo apt-cdrom add ***wich added this line in source.list:
```
deb cdrom:[APTonCD for ubuntu lucid - i386 (2010-06-22 22:26) CD1]/ /
```then:
```
sudo apt-get update
```But now if I want to install a package ***sudo apt-get install xorg*** for exemple, 
I have many lines of errors like:
```
Impossible to retrieve cdrom:[APTonCD for ubuntu lucid - i386 (2010-06-22 22:26) CD1]/packages/package_name.deb

```What's that problem ? :confused:

Thanks

---

### Post by nidzo732 on 2010-06-23
When you insert cd you will get a prompt to start package manager.
Accept the prompt , and then synaptic will be started. Click on the origin button and click on one of the lines that have APTonCD in their name (main(aptoncd for ubuntu),contrib(aptoncd for ubuntu) etc.). If this won't work browse the "Packages" folder on the cd, everything is there.

---

### Post by duddy67 on 2010-06-23
Thanks for you response.
> When you insert cd you will get a prompt to start package manager.
Unfortunately I don't have any prompt at all. :confused:
I noticed that after the ***sudo apt-cdrom add*** command, an /apt repertory as been created 
in the /media repertory. But it remains empty when I insert the CD.
Did I missed something ?

Any idea ?

---

### Post by nidzo732 on 2010-06-23
Try using software sources (system>administration>software sources) and select "add cd" under "other software" tab. Then start synaptic click the
"origin" button and find apt on cd. If this won't work install APTonCD  forom "packages" folder on the cd(dependencies should be on the cd too).
Start the APTonCD and select "restore" button , then click "load" and select
CD (or image), then  click restore. Packages will be copied to APT cache (so they don't need to be downloaded). After that use synaptic to install packages (it should say 0kb to download).

---

### Post by duddy67 on 2010-06-24
Thanks again.:p

The software sources solutions seems to work. I retrieve, in Synaptic, the packages I burned on the CD.
But if I start the install I get the "failed to mount cdrom" message. :shock:
So I'm afraid I have to handle 2 pb at the same time.
However this cdrom pb might be the source of the install packages pb.

I think I have to dive deeply into it to find a working solution. :?

---

### Post by nidzo732 on 2010-06-24
Try installing APTonCD from the "packages" folder on the cd
(dependencies are alssothere).Start the APTonCD and select "restore" button , then click "load" and select
CD (or image), then click restore. Packages will be copied to APT cache (so they don't need to be downloaded). After that use synaptic to install packages (it should say 0kb to download).

---

### Post by nidzo732 on 2010-06-24
If the previous post won't work innstall manualy from the packages
folder on the cd.

---

### Post by duddy67 on 2010-08-18
I re up that post again.
I'm retrying to use an APTonCD repository cd in order to install 
package on a internetless PC (with no graphical interface).
So when I type: sudo apt-cdrom add I get 
    > Utilisation du point de montage /media/apt/ pour le cédérom
    Identification...[d872c9d3e1ce2bbae624727558988899-2]
    Examen du disque à la recherche de fichiers d'index...
    1 index de paquets trouvés, 0 index de sources, 0 index de traductions et 0 signatures
    Ce disque s'appelle :
    « APTonCD for ubuntu lucid - i386 (2010-08-16 09:12) CD1 »
    Reading Package Indexes... Fait
    Écriture de la nouvelle liste de sources
    Les entrées de listes de sources pour ce disque sont :
    deb cdrom:[APTonCD for ubuntu lucid - i386 (2010-08-16 09:12) CD1]/ /
    Veuillez répéter cette opération pour tous les disques de votre jeu de cédéroms.
wich seems ok.
But when I want to install some package (sudo apt-get install xorg for ex) 
I get:
> Err cdrom://[APTonCD for ubuntu lucid - i386 (2010-08-16 09:12) CD1]/ So what is that damn error ? :evil:


Thanks for helping

---

### Post by e.m.fields on 2010-10-05
Hey. 
I hope you have this solved by now, but if not:
I discovered that it may have something to do with DVD vs CD iso. 
I created an apt-on-cd repository "one DVD" sized iso, and synaptic did not want to accept it. It would continue to prompt me for "insert a cd" when I tried to add a repository, so this would not work.

I found some useful instructions on how to use synaptic from an ISO image here:
[http://hewetson.blogspot.com/2008/05/use-synaptic-package-manager-with-iso.html](http://hewetson.blogspot.com/2008/05/use-synaptic-package-manager-with-iso.html)

I also suggest Keryx. this seems to be the ticket.
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by jdunlap on 2011-01-11
I had the same problem.  Cured it by copying the entire (unmounted) CDROM using dd to an .iso file.  Now aptoncd works from the .iso file.  Before, when trying to use the CDROM directly, aptoncd failed saying it couldn't mount the CDROM.  Trouble was, it was already mounted via the automatic mechanism.  Even Synaptic had problems with some of the files on the CDROM: Some worked and some didn't.  But, once aptoncd had copied them from the .iso to the apt cache then Syncaptic worked fine.

---

### Post by DarellCraighead on 2011-03-16
I am having a very similar problem trying to restore on my netbook.  My netbook does not have a CDROM so I want to restore from the .iso file I created on another system.  Problem is, when I click RESTORE then click LOAD nothing happens???  I do not get the prompt window for the restore media.  Anyone know a solution for this?

---

