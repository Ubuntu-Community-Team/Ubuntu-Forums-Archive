---
title: "Environmental variables and sudo"
date: 2009-11-07
forum: General Help
---

### Post by is-serp on 2009-11-07
Hi all,

I am encountering an annoying problem on my Ubuntu Linux. 

I am a Java developer and set up my box with all the tools I need to do my job. I installed tools such as Apache Ant in the /opt directory and then added the ANT_HOME variable in the /etc/enviroment file, and modified the value of the PATH variable in the same file by appending $ANT_HOME/bin.

When I was done with this, I executed the command 

```

source /etc/enviroment
```

to reload the configuration. Now when I try to invoke ant from the command line, it works fine. However, if I need root permissions to run a particular ant script (say to start a TCP listener on port 80), and use sudo to execute ant, I get a command not found error. Any ideas on how to fix this?

Thanks for your time. I am using 9.10 64-bit, but had the same problem with 9.04 x86.

---

### Post by lloyd_b on 2009-11-07
Try "sudo -E ..." rather than a standard "sudo ...".  By default, 'sudo' resets the environment (I assume for security reasons), and the "-E" option overrides this reset.

Lloyd B.

---

### Post by is-serp on 2009-11-07
Hi Lloyd,

Thanks for you reply, but it still didn't work :(. Am still getting a command not found error.

Also this is the first time I am putting my variables in /etc/enviroment as usually I use /etc/profile. Not I just noticed that a /etc/enviroment was not read on log-in, i.e. to run ant even without sudo, first I had to source /etc/enviroment. Is there a logical reason behind that?

//josef

---

### Post by is-serp on 2009-11-08
Also, what I'm finding really strange in all of this is that if I execute sudo echo $ANT_HOME, I resolves the variable and gives me the path to ant, and if I do sudo echo $PATH, there is the ant bin folder in the path. So somehow it seems as if sudo is ignoring that $PATH variable and using a different search space.

Any knows how to handle this?

---

### Post by is-serp on 2009-11-08
Ok so I just found out by googling the problem that sudo -i achieves what I want.

Is there any way (other than using an alias) to get the -i behaviour by default?

---

