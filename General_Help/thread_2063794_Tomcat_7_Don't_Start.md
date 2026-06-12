---
title: "Tomcat 7 Don't Start"
date: 2012-09-27
forum: General Help
---

### Post by javapaulomg on 2012-09-27
Hi Friends,

   I'm trying to start "Tomcat 7" service, the application folder, has inside my user folder, i build a file named "Start_Services", inside the flder "/etc/init.d/", but he don't execute automatic, only manual using console, after autenticate, i need to know, how i can make it run automatic, ou i'm doing something wrong? Another detail is, the "Tomcat" only start automatic when he inside "opt" folder.

P.S: Sorry for my poor english :-)

Command:

```

sudo /etc/init.d/Start_Services start

```

File "Start_Services":

```

# description: Auto-starts tomcat
# processname: tomcat
# pidfile: /var/run/tomcat.pid

# Conteúdo do arquivo de execução
#!/bin/sh

HOME_PROGRAMAS=/opt/
TOMCAT_PATH=/home/desenvolvimento/programas/apache-tomcat-7.0.30/bin
SONAR_PATH=sonar-3.2/bin/linux-x86-32
NEXUS_PATH=/home/desenvolvimento/nexus-2.1.2-bundle/nexus-2.1.2/bin/jsw/linux-x86-32

case $1 in
start)
 *#TomCat#
 *echo “Iniciando TomCat”
 *sudo -u desenvolvimento sh $TOMCAT_PATH/startup.sh
 *#

 *#Sonar#
 *echo “Iniciando Sonar”
 *#sh $HOME_PROGRAMAS$SONAR_PATH/sonar.sh start
 *#

 *#Nexus#
 *echo “Iniciando Nexus”
 *#sudo -u desenvolvimento $NEXUS_PATH/nexus start
 *#
 *;;
stop)
 *#TomCat#
 *echo “Parando TomCat”
 *sudo -u desenvolvimento sh $TOMCAT_PATH/shutdown.sh
 *#

 *#Sonar#
 *echo “Parando Sonar”
 *#sh $HOME_PROGRAMAS$SONAR_PATH/sonar.sh stop
 *#

 *#Nexus#
 *echo “Parando Nexus”
 *#sudo -u desenvolvimento $NEXUS_PATH/nexus stop
 *#
 *;;
restart)
 *$0 stop
 *$0 start
 *;;

*)
echo $”Utilize uma das opções $0 {start|stop|restart}”
exit 3
;;

esac
:

```

---

