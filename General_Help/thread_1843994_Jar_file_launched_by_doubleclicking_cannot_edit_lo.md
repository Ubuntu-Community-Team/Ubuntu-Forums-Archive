---
title: "Jar file launched by doubleclicking cannot edit local file"
date: 2011-09-14
forum: General Help
---

### Post by Vigneshwaran on 2011-09-14
Hi,
I am a developer of this application [NeembuuUploader]("http://neembuuuploader.sf.net/"). My application stores settings in a settings/settings.dat local file and user passwords in a properties file in user's home directory. If I launch the application by double clicking the jar file, I find that it cannot read or write to the local file whereas it can do both with the property file in user's home directory.

This does not happen when I tested with Windows 7 and MacOS X Snow Leopard (and in Ubuntu itself if I launch from terminal.) I don't know if this will be the case with all other linux distros. So I am waiting to release the latest build.

Can anybody help me out with this?

---

### Post by ofnuts on 2011-09-14
> **Vigneshwaran said:**
> Hi,
I am a developer of this application [NeembuuUploader]("http://neembuuuploader.sf.net/"). My application stores settings in a settings/settings.dat local file and user passwords in a properties file in user's home directory. If I launch the application by double clicking the jar file, I find that it cannot read or write to the local file whereas it can do both with the property file in user's home directory.

This does not happen when I tested with Windows 7 and MacOS X Snow Leopard (and in Ubuntu itself if I launch from terminal.) I don't know if this will be the case with all other linux distros. So I am waiting to release the latest build.

Can anybody help me out with this?Depends how you are accessing it... (and what you definitions of "local file" is). IIRC by default Windows launches apps with the current directory set to the directory where the app is (which is a Bad Thing) while Linux starts them in the user's home directory.

When you say "My application stores settings in a settings/settings.dat local file", this, in Linux, implies "somewhere under the user's home directory". If it's for all users (but read-only) there it goes in /usr/share, while the app code is split beteen /usr/bin and /usr/lib.

---

### Post by Vigneshwaran on 2011-09-14
By "local file", I meant.. umm.. a file in the application directory only. I don't know how else to say. The java code I use to access the file is
```
new File("settings/settings.dat");
```

This will search for the settings.dat file inside settings directory present in the application directory. This is how it works in Windows and Mac.

But you say that in linux this will search for the file in user's home directory. If that is correct, then why does it work when launched from terminal alone? :confused:

---

### Post by Azdour on 2011-09-15
Hi,

I've had path issues before with Java and applications. In the end I had to write a simple script to launch the application:

cd <directory of application>
java ....

Without doing the 'cd' Java could not locate files using the relative path, e.g in your instance 'settings/settings.dat'

I could then create a desktop launcher to call the script.

I wonder if this is the problem you are facing?

---

### Post by Vigneshwaran on 2011-09-15
not quite.. :(

---

### Post by ofnuts on 2011-09-15
> **Vigneshwaran said:**
> By "local file", I meant.. umm.. a file in the application directory only. I don't know how else to say. The java code I use to access the file is
```
new File("settings/settings.dat");
```This will search for the settings.dat file inside settings directory present in the application directory.No, this searches the **current directory**, which just happens to be the directory where your executable is, *by default*. The user could make a shortcut with a different working directory (for instance, where he keeps files to upload).

> **Vigneshwaran said:**
> This is how it works in Windows and Mac.By luck, and until the user tries to change things.

> **Vigneshwaran said:**
> But you say that in linux this will search for the file in user's home directory.No I say that in Linux, this also searches the **current directory**, which just happens to be the user's home directory, *also by default*, and in Linux also, there are ways to create shortcuts to start apps with a given working directory.

> **Vigneshwaran said:**
> If that is correct, then why does it work when launched from terminal alone? :confused:What was the current directory when you started the app from a terminal?

Actually, in Java, if you need to reference a file that came with your code, you put it somewhere in your classpath and use [getResourceAsStream()]("http://download.oracle.com/javase/1.4.2/docs/api/java/lang/ClassLoader.html#getResourceAsStream%28java.lang.String%29") and such like to reference it. OK, this is a chicken-and-egg problem because you know have to define the class path (if the file is outside your JAR), but this is usually solved by a cover script/bat that calls Java with a proper classpath (and possibly other useful options). One benefit for the user is that the application started is really an executable and double-clicking it will always start it, while double clicking JARs don't always work as you expect: I have seen systems where this opens them in WINZIP/WINRAR, or where this start the smartphone software installer... It also makes it easier to set a working directory.

---

### Post by Vigneshwaran on 2011-09-15
Thanks. I will try that method.

>  I have seen systems where this opens them in WINZIP/WINRAR, or where this start the smartphone software installer... It also makes it easier to set a working directory.

Yes. WinZip/WinRar/Archive Mounter/Nokia Software installer associate themselves with the .jar extension. We have to change the association to Java runtime.

---

### Post by ofnuts on 2011-09-16
> **Vigneshwaran said:**
> Thanks. I will try that method.



Yes. WinZip/WinRar/Archive Mounter/Nokia Software installer associate themselves with the .jar extension. We have to change the association to Java runtime.A much better solution is a cover script, IMHO, so you can leave the association alone, and are not at the mercy of a later (re-)installation/upgrade of another software that resets it.

---

