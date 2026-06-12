---
title: "Set Java path for all users (including root)"
date: 2010-01-27
forum: General Help
---

### Post by esauer on 2010-01-27
I am trying to set my java path so that it is in effect for all users including the root user. I set the path correctly in /etc/profile and that works for my personal user, but when i try to run the same commands using sudo, i get messages saying that it can't find the java path.

Can someone help me please?

---

### Post by ratcheer on 2010-01-27
Interesting question. It seems that root uses the same .profile as the normal user. So, root should get the same java path.

I will have to reboot to investigate further (because I, too, just upgraded my Java) and I don't want to reboot, right now. I will try to remember to follow up, later.

Tim

---

### Post by ratcheer on 2010-01-27
Ok, you are absolutely correct. Setting the Java path for the primary user does not also set it for root. If you are connecting as root, a different .profile is executed from "/root". I am not sure whether this is the same as / or is a subdirectory of /

So, to add Java to root's $PATH, I added the following to /root/.profile

```

JAVA_HOME=/opt/jre-6u18/jre1.6.0_18
PATH=$JAVA_HOME/bin:$PATH

```However, I am unsure whether this will be effective when using sudo to do something. I do know that it works if you enter a shell as root.

Also, note that my JAVA_HOME specification is where I installed Java. Yours might be different.

Tim

---

### Post by sisco311 on 2010-01-27
By default, sudo resets the PATH environment variable.

You can use *sudo -i command* or set the PATH in the sudoers file with the secure_path option.

---

