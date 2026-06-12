---
title: "Erros installing JasperServer pro 4.0, may be a problem with Ubuntu 10.04 setup"
date: 2011-02-14
forum: General Help
---

### Post by juicyoner on 2011-02-14
Hi there - 

I'm trying to install (not upgrade) Jasper server pro 4.0, and I keep getting these annoying errors. I suspect they have something to do with my Ubuntu setup (I'm using 10.04) rather than Jasper so I figured I'd try asking around here.

For example when I run the install script: "./js-install.sh test":

--
[B]
./bin/do-js-install.sh: 30: [[: not found
./bin/do-js-install.sh: 30: pro: not found
[: 72: test: unexpected operator
./bin/do-js-setup.sh: 93: [[: not found
./bin/do-js-setup.sh: 93: 4: not found
./bin/do-js-setup.sh: 98: [[: not found
./bin/do-js-setup.sh: 103: [[: not found[/B]
Writing to log file: logs/js-install-pro_2011-02-14_14-01-10000.log
[: 127: unexpected operator

[: 128: Running JasperReports Server install script at 2011-02-14_14-01: unexpected operator
Running JasperReports Server install script at 2011-02-14_14-01
[: 129: unexpected operator

[: 136: /usr/local/lib/jdk: unexpected operator
[: 141: [test]: unexpected operator
[test]
[: 143: Running pre-install-test-pro Ant task.: unexpected operator
Running pre-install-test-pro Ant task.
[: 143: unexpected operator

Buildfile: /home/kburns/jasperreports-server-4.0/buildomatic/build.xml
     [echo] Filtering properties (cleaning out blank spaces)

test-pro-all-props:
     [echo] Checking properties:
     [echo]   appServerType=tomcat6
     [echo]   appServerDir=/home/tomcat
     [echo]   dbType=mysql
     [echo]   dbHost=localhost
     [echo]   dbUsername=root
     [echo]   dbPassword=**********
     [echo]   dbPort=3307
     [echo]   js.dbName=jasperserver40
     [echo]   sugarcrm.dbName=sugarcrm
     [echo]   foodmart.dbName=foodmart
     [echo]   webAppNamePro=jasperserver-pro
check-dbtype-pro:

test-appServerType-pro:

do-pre-install-test:
     [echo] Checking DBMS host and port:
     [echo]   Host localhost is OK

BUILD FAILED
/home/kburns/jasperreports-server-4.0/buildomatic/bin/validation.xml:276: The following error occurred while executing this line:
/home/kburns/jasperreports-server-4.0/buildomatic/bin/validation.xml:42: The following error occurred while executing this line:
/home/kburns/jasperreports-server-4.0/buildomatic/bin/validation.xml:88: Error: port 3307 is not reachable at host localhost

Total time: 0 seconds
[B][: 143: Checking Ant return code: OK: unexpected operator
Checking Ant return code: OK
[: 144: unexpected operator[/B]


--

Note all the problems with "[[: not found" and "[: 144: unexpected operator"

Has anyone ever come across this?

---

### Post by juicyoner on 2011-02-16
Turns out this is a known issue specific to Ubuntu, although the Jasper people will be fixing it in the new release coming out in march.

[http://jasperforge.org/plugins/espforum/view.php?group_id=112&forumid=102&topicid=84027&topid=84095](http://jasperforge.org/plugins/espforum/view.php?group_id=112&forumid=102&topicid=84027&topid=84095)

From the above link...

[I][INDENT]Yes, sorry this is a bug in the initial release of JasperServer Pro 4.0. You won't see it under JasperServer CE version (because the CE version came out afterwards and the bug was caught by then).

It only happens under Ubuntu. This is because the "auto-install" scripts try to use a bourne shell to execute (#!/bin/sh). Using bourne is an old "best practice" to try and keep backward compatibility with older Unix systems. But it turns out that under Ubuntu /bin/sh is mapped to -> /bin/dash. The Dash shell is not really fully fleshed out (at least from my taking a quick look at it). (Other linux systems map /bin/sh -> /bin/bash).

So, this bug was fixed by just going ahead and explicitly executing the Bash shell in the "auto-install" scripts.

On older Unix systems, folks can simply install a Bash shell and then they will also be able to run the "auto-install" scripts. And now, way more people are running Linux compared to old Unix instances anyway.

Lastly, the official bug fix for this issue will be coming out in the next Pro version (due sometime in March).
[/INDENT][/I]

---

