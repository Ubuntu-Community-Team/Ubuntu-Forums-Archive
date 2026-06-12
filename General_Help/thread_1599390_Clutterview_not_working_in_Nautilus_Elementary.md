---
title: "Clutterview not working in Nautilus Elementary"
date: 2010-10-17
forum: General Help
---

### Post by Melbridge on 2010-10-17
Hi, I installed Nautilus Elementary + Gloobus in Maverick with:

```
sudo add-apt-repository ppa:gloobus-dev/gloobus-preview

sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa

sudo apt-get update && sudo apt-get install gloobus-preview && sudo apt-get upgrade

nautilus -q
```

The built in terminal & gloobus preview work fine but pressing F4 for clutterview just shows a grey area at the top of the screen.
After some searching I did this:
```
gksu gedit /etc/environment
```
Then added:
```
export CLUTTER_VBLANK=none
```
to the end of the file & saved it.
Restarted Nautilus again & got this:

```
(nautilus:1537): Unique-DBus-WARNING **: Error while 
sending message: Message did not receive a reply (timeout by message bus)

```
Coverflow still doesn't work & now I'm stuck!
Any ideas :confused:

---

### Post by Melbridge on 2010-10-19
Anyone?

---

### Post by DogMatix on 2010-10-19
It mentions here, in a 'how to' info page:

> Remember, Gloobus Flow with Nautilus integration is alpha, so expect to find bugs. Also, some things such as the list below the coverflow, menu actions, etc. are not yet fully implemented. If you encounter any bugs, report them HERE. If you find the below steps too dificult, wait for the Gloobus Flow PPA!

Before we get started, please note that if you have a patched Nautilus (such as Nautilus Elementary, dual pane Nautilus or Undo/Redo Nautilus), it will not work, as you will install a new Nautilus version.

**ref:** [http://www.webupd8.org/2010/02/how-to-install-gloobus-flow-clutter.html]("http://www.webupd8.org/2010/02/how-to-install-gloobus-flow-clutter.html")

This may be a cause of your woes.

---

### Post by Melbridge on 2010-10-22
I don't know why but it is now working fine!!
Looking well cool too.

Could be an update as I just installed about 90mb!

---

### Post by Darris on 2011-03-12
is there a way to make it so integrated clutterview happens automatically?
I don't want to have to press f4 everytime.

---

### Post by fatriff on 2011-05-21
> is there a way to make it so integrated clutterview happens automatically?
I don't want to have to press f4 everytime.

This is one way to do it..

[http://ubuntuforums.org/showthread.php?t=1721799](http://ubuntuforums.org/showthread.php?t=1721799)

---

