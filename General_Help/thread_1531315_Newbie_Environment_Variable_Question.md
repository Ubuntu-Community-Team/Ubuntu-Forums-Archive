---
title: "Newbie Environment Variable Question"
date: 2010-07-14
forum: General Help
---

### Post by giesen2 on 2010-07-14
I want to set JDK_HOME for IntelliJ IDE.

I googled some Ubuntu docs, and the recommended way to set a system wide environment variable is in /etc/environment.

I add to /etc/environment:
JDK_HOME=/usr/lib/jvm/java-6-sun

then run
source /etc/environment

now I can see the variable is set like this:
echo $JDK_HOME
but if I do this it's not set
env | grep JDK
also, IDEA won't startup

If I do this
export JDK_HOME=$JDK_HOME
then both "env | grep JDK" and IDEA work.

How do I properly configure my system so that the JDK_HOME variable is properly configured on startup/login without extra manual command line steps?

I'm reading [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
and it says that modifying ~/.profile ~/.bashrc ~/.bash_profile /etc/profile or /etc/bash.bashrc is not recommended.

I know this is a simple issue and there is a ton of articles on this simple material, but I've read dozens of them and it is not clear. Thanks!

Thanks!

---

### Post by WorMzy on 2010-07-14
Just adding them to /etc/environment works for me, you just need to logout and back in for them to take effect.

---

### Post by giesen2 on 2010-07-14
> **WorMzy said:**
> Just adding them to /etc/environment works for me, you just need to logout and back in for them to take effect.

You are correct.

Is there a way to get the new environment variable to take affect without doing a full logout? I read that running "source /etc/environment" would do the trick, but obviously that doesn't completely work.

---

### Post by WorMzy on 2010-07-14
I can't find a way of adding it to env while logged in, but you can add it to your current terminal by declaring it. I would have thought 'export' or 'set' would do the trick, but neither seems to persist outside of the current terminal, and certainly doesn't affect other users. Sorry, but unless someone else can shed some light on this matter, I think logging out and back in is only way to update env.

---

