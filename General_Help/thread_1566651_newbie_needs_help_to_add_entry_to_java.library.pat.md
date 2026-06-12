---
title: "newbie needs help to add entry to java.library.path"
date: 2010-09-02
forum: General Help
---

### Post by xi4 on 2010-09-02
Hi. I have received the following instructions:

Copy the files to somewhere handy and add the natives to your java.library.path

the file in question is a .so Its needed for a Java API I am trying to install

How do I do this?


help appreciated

---

### Post by akoskm on 2010-09-02
> **xi4 said:**
> Hi. I have received the following instructions:

Copy the files to somewhere handy and add the natives to your java.library.path

the file in question is a .so Its needed for a Java API I am trying to install

How do I do this?


help appreciated

Are you trying to do this in Eclipse or manually by editing the .classpath file?

---

### Post by xi4 on 2010-09-02
ideally i'd like to do this so that it will run both in eclipse and not.

there's a .classpath? - I really am a ubuntu noob. Im also not too good at dev environment set up.

---

### Post by akoskm on 2010-09-03
> **xi4 said:**
> ideally i'd like to do this so that it will run both in eclipse and not.

there's a .classpath? - I really am a ubuntu noob. Im also not too good at dev environment set up.

.classpath is a hidden file inside the projects directory - I never modify this file directly.
I more prefer the Eclipse-way:
In the **Window** menu select **Preferences**, type *libraries* into the search form, and select **User Libraries**, click to **New**, name it. By clicking to the **Add JARs...** you can specify the path to the libraries. This is the regular way to define a User Library inside Eclipse.
To add the defined library: right click to your project, **Build Path** > **Add Libraries** select User Libraries and check the libraries what you want to add to the classpath.

---

### Post by xi4 on 2010-09-05
ah yes, but it's not a jar file. it's a SO file, whatever that is.

---

