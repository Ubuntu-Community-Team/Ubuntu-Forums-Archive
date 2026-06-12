---
title: "maven doesn't see JAVA_HOME variable ubuntu 11.10"
date: 2012-01-08
forum: General Help
---

### Post by mahomet on 2012-01-08
Hi,

when i execute command 
```
mvn --version
```
i get a warning

```
JAVA_HOME environment variable is not set.
```
i have exported JAVA_HOME variable 

```
mht@mht-ThinkPad-T400:~$ echo $JAVA_HOME
/work/apps/jdk1.6.0_30
```

path looks like this:

```
echo $PATH
/work/apps/jdk1.6.0_30/bin:/work/apps/apache-maven-2.2.1/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Have any one knows why maven ignores JAVA_HOME?

Regards

---

