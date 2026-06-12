---
title: "Cannot write file with Java using Tomcat 7"
date: 2012-02-15
forum: General Help
---

### Post by Newbie2011 on 2012-02-15
Hi,

I am using Tomcat 7 on Ubuntu 11.10. With Java 1.6 I created an application that should write a file into its WEB-INF folder as deployed on Tomcat.

In Java 

```
file.canWrite();
```

returns false.

After checking file permissions in Ubuntu (rw is permitted for the tomcat user), I edited the /etc/tomcatuser/03catalina.policy file by adding:

```
grant codeBase "file:${catalina.base}/webapps/Projectname" {
java.io.FilePermission "${catalina.base}/webapps/Projectname$/WEB-INF/foldername", "read, write";
};
```

It does not make any difference. When I try to write a file I get a FileNotFoundException.

---

### Post by Newbie2011 on 2012-02-16
Alright, never mind.

I got confused with the tomcat directory structure in ubuntu and now solved the problem.

---

