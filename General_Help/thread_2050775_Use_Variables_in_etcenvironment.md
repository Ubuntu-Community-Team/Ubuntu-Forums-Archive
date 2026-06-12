---
title: "Use Variables in /etc/environment?"
date: 2012-08-31
forum: General Help
---

### Post by noloader on 2012-08-31
Hi All,

I'm having problems using variables in /etc/environment.

Could anyone point out my mistake(s)?

Thanks in advance,
Jeff

jeffrey ~ $ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:$JAVA_HOME/bin:$JAVA_HOME/lib:$JDK_HOME/bin:$JDK_HOME/lib:$ANDROID_SDK/tools:$ANDROID_SDK/platform-tools:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
jeffrey ~ $ cat /etc/environment
export JAVA_HOME=/opt/java/64/jre1.7.0_07
export JDK_HOME=/opt/java/64/jdk1.7.0_07
export ANDROID_SDK=/opt/android-sdk
export ANDROID_NDK=/opt/android-ndk
export PATH="/usr/local/sbin:/usr/local/bin:$JAVA_HOME/bin:$JAVA_HOME/lib:$JDK_HOME/bin:$JDK_HOME/lib:$ANDROID_SDK/tools:$ANDROID_SDK/platform-tools:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
jeffrey ~ $ source /etc/environment
jeffrey ~ $ echo $PATH
/usr/local/sbin:/usr/local/bin:/opt/java/64/jre1.7.0_07/bin:/opt/java/64/jre1.7.0_07/lib:/opt/java/64/jdk1.7.0_07/bin:/opt/java/64/jdk1.7.0_07/lib:/opt/android-sdk/tools:/opt/android-sdk/platform-tools:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by papibe on 2012-08-31
Hi noloader.

'/etc/environment' is not a script, but a list of global variables. Try this syntax:
```
JAVA_HOME=/opt/java/64/jre1.7.0_07
JDK_HOME=/opt/java/64/jdk1.7.0_07
ANDROID_SDK=/opt/android-sdk
ANDROID_NDK=/opt/android-ndk
PATH="/usr/local/sbin:/usr/local/bin:$JAVA_HOME/bin:$JAVA_HOME/lib:$JDK_HOME/bin:$JDK_HOME/lib:$ANDROID_SDK/tools:$ANDROID_SDK/platform-tools:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```
Then restart your machine.

Let us know how it goes.
Regards.

---

### Post by noloader on 2012-08-31
Hi papibe,

No joy.

Jeff

---

### Post by diesch on 2012-08-31
*/etc/environment* is not read by a shell but by *pam_env*.  Shell variables like *$JAVA_HOME *do not get expanded even if you define them there.

You have to use */opt/java/64/jre1.7.0_07/bin* instead of *$JAVA_HOME/bin*

---

### Post by mku1tra on 2012-09-18
Same happened to me, setting the variable in environment did not work at all. 
I set the path of JAVA_HOME in .bashrc and so far most java apps seem to work alright. Give it a try. Would work, providing you use bash that is

---

