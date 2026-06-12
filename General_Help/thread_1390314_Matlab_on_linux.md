---
title: "Matlab on linux?"
date: 2010-01-25
forum: General Help
---

### Post by trex93 on 2010-01-25
I am trying to install matlab onto my personal laptop. When i start to download i get a file "download_agent" i have updated my java to the most recent edition and when i run "javaws download_agent" i get this error :

[B][I]net.sourceforge.jnlp.LaunchException: Fatal: Launch Error: Could not launch JNLP file.
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:395)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:623)
Caused by: java.lang.IllegalAccessException: Class net.sourceforge.jnlp.Launcher can not access a member of class com.mathworks.agent.AgentGUI with modifiers "public static"
    at sun.reflect.Reflection.ensureMemberAccess(Reflection.java:95)
    at java.lang.reflect.Method.invoke(Method.java:607)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:387)
    ... 1 more
Caused by: 
java.lang.IllegalAccessException: Class net.sourceforge.jnlp.Launcher can not access a member of class com.mathworks.agent.AgentGUI with modifiers "public static"
    at sun.reflect.Reflection.ensureMemberAccess(Reflection.java:95)
    at java.lang.reflect.Method.invoke(Method.java:607)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:387)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:623)[/I][/B]

Thanks so much for your help!

---

### Post by RabbitWho on 2010-01-25
I don't want to spam your thread.. I just wanted to mention I thought that said "methlab" first.. anyway I think you'll get more help in one of the support forums.

---

### Post by Xbehave on 2010-01-25
I have no idea wrt to that error but have you tried
[https://help.ubuntu.com/c/javaommunity/MATLAB](https://help.ubuntu.com/c/javaommunity/MATLAB)

---

### Post by wgarn on 2010-05-10
I have got the same problem - did you find a solution? 
Mathworks suggests the workaround to manually download, etc.

Executing:  javaws download_agent.jnlp
this downloads five jar files resulting in ... 
Launch Error: Could not launch JNLP file.Launcher can not access a member of class 
com.mathworks.agent.AgentGUI with modifiers "public static"

Location of JAR files:  /home/YOUR-USER-NAME/.netx/cache/http/www.mathworks.com/
Location of AgentGUI: in agent_20090414.jar 
The jar file has com.mathworks.agent.AgentGUI as main-class in the manifest.mf

Any ideas what could be wrong?

---

### Post by cguy on 2010-05-10
While the Linux version will give you countless headaches (I've wasted many hours to make it work), the Windows version works perfectly in Wine.
Save yourself the time! ;)

---

### Post by MaxIBoy on 2010-05-10
Supposedly, GNU Octave is a free replacement. I haven't tried it myself, though, so I can't say how similar it is or how good it is.

---

### Post by Random_Dude on 2010-05-10
> **MaxIBoy said:**
> Supposedly, GNU Octave is a free replacement. I haven't tried it myself, though, so I can't say how similar it is or how good it is.

It's ok, but Matlab has an GUI. Which may sound irrelevant, but it's really more productive.
It also has some extra packages for doing more advanced stuff, but I never used them so...

Still, I'm no Matlab expert. I'm sure someone can give a more detailed comparison.

Cheers :cool:

---

### Post by Random_Dude on 2010-05-10
EDIT: Sorry double post.

---

### Post by jpeddicord on 2010-05-10
*Thread moved to **General Help**.*

---

### Post by wgarn on 2010-05-17
> **cguy said:**
> While the Linux version will give you countless headaches (I've wasted many hours to make it work), the Windows version works perfectly in Wine.
Save yourself the time! ;)
                                  Thank you for the tip - cguy. I thought that I could run my Matlab version from my Vista partition, but it seems that I was mistaken...
 *&#8220;Error: Unable to reserve shield memory - disabling shield (line:760) System Error: 487, Invalid address &#8221;*, but I have also got a "MathWorks Software Activation" dialogue, which is unreadable (changing the screen resolution does not help). In my Wine configuration I have got the Windows Vista  version, otherwise the default settings. That means the C: drive is mapped to a folder on my Ubuntu partition, which is not &#8220;easy&#8221; to change. I had a look at the[COLOR=Blue]** [Wiki-Wine site]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2") **[/COLOR]and it states that I should not try to change it, otherwise I will "break" my Windows operating system. So I guess that I have to reinstall Matlab!? &#8220;cguy&#8221; are you aware of any constraints or performance issues under Ubuntu? (I have actually changed to Ubuntu because of its speed and stability.)

---

