---
title: "Which JAVA to Choose?"
date: 2011-12-31
forum: General Help
---

### Post by feartheterrapin on 2011-12-31
I understand why Oracle’s Sun Java JDK packages were removed from the Ubuntu partner repositories and disabled on users systems.  However, many applications and web sites do not function properly using openjdk-6.  I know I can manually install sun-java, but I prefer my installations via the Canonical.  It is my understanding that openjdk-7 will soon be available via the Canonical.  There was an earlier quote, *“Oracle themselves will be using OpenJDK as the basis for their own future releases.”*.  Does this mean  openjdk-7 will fix all the incompatibilities between Sun and OpenJDK?

---

### Post by whatthefunk on 2011-12-31
> **feartheterrapin said:**
> I know I can manually install sun-java, but I prefer my installations via the Canonical.  It is my understanding that openjdk-7 will soon be available via the Canonical.

openjdk is already in the Ubuntu repositories.

---

### Post by BC59 on 2011-12-31
I installed Oracle Java 7 manually and I can wait now for Canonical to find a solution.

---

### Post by whatthefunk on 2011-12-31
> **BC59 said:**
> I installed Oracle Java 7 manually and I can wait now for Canonical to find a solution.

Is it Canonical's responsibility to find a solution to a problem that is not in their hands?  Canonical has nothing to do with either Java program.  Software developers and Oracle need to work together to find a solution.

---

### Post by vpharry on 2011-12-31
> **whatthefunk said:**
> Is it Canonical's responsibility to find a solution to a problem that is not in their hands?  Canonical has nothing to do with either Java program.  Software developers and Oracle need to work together to find a solution.
I think Canonical and oracle both have to sort out the mess...

---

### Post by BC59 on 2011-12-31
> **whatthefunk said:**
> Is it Canonical's responsibility to find a solution to a problem that is not in their hands?  Canonical has nothing to do with either Java program.  Software developers and Oracle need to work together to find a solution.

> Oracle, in retiring the ‘Operating System Distributor License for Java’, means Canonical no longer have permission to distribute the package.

Oracle already answered and now has nothing to do. 
The developers have nothing to do with the legal issues.
Canonical is building Ubuntu so they have to find a solution for their OS.

---

### Post by Zill on 2011-12-31
> **feartheterrapin said:**
> ...Does this mean  openjdk-7 will fix all the incompatibilities between Sun and OpenJDK?
[Moving to OpenJDK as the official Java SE 7 Reference Implementation]("http://blogs.oracle.com/henrik/entry/moving_to_openjdk_as_the")
> ...In line with our strategy towards a more open Java ecosystem, we are going to provide a Reference Implementation that is based entirely on the OpenJDK open source code and make it available under the GPL open source license.

The role of the Reference Implementation (RI) is to be used as the gold standard for all Java implementations...

---

### Post by sammiev on 2011-12-31
A lot of programs require JRE Java or what some people call Sun Java. If needed the [manual]("http://sites.google.com/site/easylinuxtipsproject/java") way is the only way. :)

---

### Post by feartheterrapin on 2011-12-31
> **sammiev said:**
> A lot of programs require JRE Java or what some people call Sun Java. If needed the [manual]("http://sites.google.com/site/easylinuxtipsproject/java") way is the only way. :)

What I am understanding is that the incompatibilities between JRE (Sun) JAVA and Open-JDK are anticipated to remain through the next Open-JDK release.  Is that a fair analysis?

---

### Post by sammiev on 2011-12-31
You need to use the java that works for you. Sun (JRE Java) will not be updated through the Repositories anymore as they lost the lic to do so. It must be done manually now. If you are a gamer or have programs that require the latest Java or JRE Java then you will need to update manually. You will find this with all Linux versions with what I seen and have read from all the different OS.

---

### Post by whatthefunk on 2011-12-31
> **BC59 said:**
> Oracle already answered and now has nothing to do. 
The developers have nothing to do with the legal issues.
Canonical is building Ubuntu so they have to find a solution for their OS.

But this isnt OS specific.  For example, Minecraft needs Oracle Java.  Openjdk doesnt work for some reason.  This has absolutely nothing to do with Ubuntu.  The exact same problem happens on any other OS.

---

### Post by rsvancara on 2012-01-01
I just install the Oracle JDK.  It works....

---

### Post by jaws222 on 2012-01-01
[COLOR=Black]Yes, I have the java plugin  [COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]Version:[/FONT][/COLOR][COLOR=#000000][FONT=Arial] [/FONT][/COLOR][/COLOR][COLOR=red][FONT=Arial][COLOR=Black]1.6.0_26 on 11.10 and am prompted to apply the critical security update.  I'm pretty sure it will not work.  Does anyone know?  Also, not really sure of the purpose of the Icedtea plugin since I need the java plugin.[/COLOR]
[/FONT][/COLOR]

---

### Post by feartheterrapin on 2012-01-24
I installed Oracle JAVA.  Now JDK wants to update.  Will the JDK update over ride Oracle after the update?

---

### Post by pbrane on 2012-01-24
> **feartheterrapin said:**
> I installed Oracle JAVA.  Now JDK wants to update.  Will the JDK update over ride Oracle after the update?

If you are using Oracle Java you probably should remove OpenJDK. You should have a look at this PPA
[https://launchpad.net/~ferramroberto/+archive/java]("https://launchpad.net/~ferramroberto/+archive/java")

---

### Post by QIII on 2012-01-24
OpenJDK will not "take over".  You set the alternatives.

Do NOT uninstall OpenJDK as you will also rip out a bunch of stuff that will go away with it.

OpenJDK will do no harm unless you whistle at it and hold out a treat.

---

### Post by feartheterrapin on 2012-01-24
Open JDK and Oracle have co-existed well so far.  

Now I assume I do not want to install icedtea

---

### Post by pbrane on 2012-01-25
> **feartheterrapin said:**
> Open JDK and Oracle have co-existed well so far.  
...

OpenJDK and Oracle java should be fine installed together as QIII pointed out. use *update-alternatives * to set the default.
> **QIII said:**
> ...

Do NOT uninstall OpenJDK as you will also rip out a bunch of stuff that will go away with it.

...

I removed OpenJDK, I don't remember losing a bunch of stuff. Is it because I'm using xubuntu?

---

### Post by QIII on 2012-01-27
It may be that Xubuntu would not be problematic.

When I began recommending that site, it said to remove OpenJDK.  I told people to ignore that part.  I ran in to big problems with it, in GNOME and KDE.

At some point I happened to have contact with one of the maintainers, who told me that that part of the instructions had been removed because it was causing the problems I spoke of above.

---

### Post by inveriarity on 2012-02-05
I tried Open JDK 7 with Minecraft and the login window works but it does not want to recognize my internet.  Don't know if Oracle will work better or if it is wireless weirdness.

---

