---
title: "remote presenter application for android phones to communicate with ubuntu laptops"
date: 2011-01-23
forum: General Help
---

### Post by jvpgomes on 2011-01-23
Does any one know a good remote control for Android to use the phone as a remote presenter in talks when using an ubuntu laptop?

There are a few, but none of them are perfect.
I'd like if it could work through the bluetooth connection as sometimes there is no wi-fi connection the conference rooms.

Also, some of the existent remote presenters (working via wi fi) have very small touch keys that make it difficult for a speaker to use the application without being all the time looking at the phone to hit the key.

And would it be possible to have one of this remote presentation applications that could work through the bluetooth but without the need to have a server application, almost like a bluetooth mouse?

---

### Post by albazo on 2011-06-07
Hi,
you could try Presenter [[https://market.android.com/details?id=ratisbonsoft.presenter.full&feature=search_result]](https://market.android.com/details?id=ratisbonsoft.presenter.full&feature=search_result]). It's an easy bluetooth presenter app which focus on great usability. there is a free demoversion available.

I'am one of the programmers an we tried to build an app that basiclly runs stabile and without any mistaken inputs. The slides are controlled via touch gestures (swiping left or right). 

Sadly you have to run a (plattform independent) java server. That is because android does not support native bluetooth HID profiles.

hth, alex

---

### Post by rockprincess on 2012-03-07
[B]
EDIT: NEVERMIND, got it working ;)[/B]

hi alex,

can you please help me debug Presenter server?
i've successfully installed it by running the shell script.
after that i paired my phone with my laptop (both devices say it's paired plus i had to enter the pin).

then i ran the server, 

```
presenterServer
```
and got this little pop-up window, saying there's no active bluetooth adapter, which is just plain wrong, because i can send/accept file transfers (both directions) just fine.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213865&stc=1&d=1331147465[/IMG]

after i installed this package libbluetooth-dev, and then ran presenterServer again, i got this:
```
java.io.FileNotFoundException: guielements/logoHR.png (Permission denied)
        at java.io.RandomAccessFile.open(Native Method)
        at java.io.RandomAccessFile.<init>(RandomAccessFile.java:233)
        at javax.imageio.stream.FileImageOutputStream.<init>(FileImageOutputStream.java:69)
        at com.sun.imageio.spi.FileImageOutputStreamSpi.createOutputStreamInstance(FileImageOutputStreamSpi.java:55)
        at javax.imageio.ImageIO.createImageOutputStream(ImageIO.java:409)
        at javax.imageio.ImageIO.write(ImageIO.java:1520)
        at guielements.BtServerFrame.initTrayMenu(BtServerFrame.java:76)
        at guielements.BtServerFrame.<init>(BtServerFrame.java:47)
        at BtServerInterface.main(BtServerInterface.java:30)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader.main(JarRsrcLoader.java:58)
Exception in thread "main" java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader.main(JarRsrcLoader.java:58)
Caused by: java.lang.NullPointerException
        at javax.imageio.ImageIO.write(ImageIO.java:1528)
        at guielements.BtServerFrame.initTrayMenu(BtServerFrame.java:76)
        at guielements.BtServerFrame.<init>(BtServerFrame.java:47)
        at BtServerInterface.main(BtServerInterface.java:30)
        ... 5 more

```

---

### Post by mbernasocchi on 2012-06-03
> **rockprincess said:**
> [B]
EDIT: NEVERMIND, got it working ;)[/B]


How?
thanks a lot

---

