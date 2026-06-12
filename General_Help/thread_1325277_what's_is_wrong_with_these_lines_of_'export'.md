---
title: "what's is wrong with these lines of 'export'"
date: 2009-11-13
forum: General Help
---

### Post by iamgzy on 2009-11-13
so that there always error message like 'bash: export: `/home/zy/apache_ant_1_7_1/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games': not a valid identifier' ?

i put them in ~/.bashrc, is that the problem?

export ANT_HOME=/home/zy/apache_ant_1_7_1
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export CLASSPATH=/usr/lib/jvm/java-6-sun/lib
export PATH= $ANT_HOME/bin:$PATH

---

### Post by iamgzy on 2009-11-13
up !

---

### Post by hwttdz on 2009-11-13
It's the space after the equals in the last line.  Remove the space, should be good to go.

---

### Post by iamgzy on 2009-11-13
awesome, you are my boss

---

