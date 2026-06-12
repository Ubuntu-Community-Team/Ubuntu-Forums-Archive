---
title: "Help, Tutorial connect PHP 5 with MySQL Cluster"
date: 2011-06-13
forum: General Help
---

### Post by nvanvanohe on 2011-06-13
Hello everybody, I have a problem with MySQL Cluster 7.1.9 of distribution Ubuntu Server 11.04.

I can't access to MySQL Cluster on PHP. I can configure MySQL Cluster with a tutorials on Internet [http://www.awven.com/q141-crear-un-cluster-mysql-ubuntu-server-1104/](http://www.awven.com/q141-crear-un-cluster-mysql-ubuntu-server-1104/), I connect 2 nodes storage (two PCs), 1 management node (one PC), but I can't configure the MySQL Server to access way PHP, I searched tutorial about this.

To configure my servers I do it:

**One Management Node**
1.- Install Ubuntu Server Natty 11.04 with LAMP option.
2.- Install MySQL Server.
     sudo apt-get install mysql-server
3.- Install MySQL Cluster Server.
     sudo apt-get install mysql-cluster-server
4.- Configure /etc/mysql/ndb_mgmd.cnf

[NDBD DEFAULT]
NoOfReplicas=2 (En este caso de ejemplo, cambie segun el numero de nodo de datos
DataMemory=256M
IndexMemory=18M 
[MYSQLD DEFAULT]
[NDB_MGMD DEFAULT]
[TCP DEFAULT]
# Sección para la configuración del nodo de administración
[NDB_MGMD]
# IP del nodo de administracion
HostName=192.168.1.1 #Cambiar por la ip que desee
[NDBD]
 # IP del primer nodo de datos
 HostName=192.168.1.2 #Cambiar por la ip que desee
 DataDir=/var/lib/mysql-cluster
 BackupDataDir=/var/lib/mysql-cluster/backup
 DataMemory=512M
 [NDBD]
 # IP del segundo nodo de datos
 HostName=192.168.1.3 #Cambiar por la ip que desee
 DataDir=/var/lib/mysql-cluster
 BackupDataDir=/var/lib/mysql-cluster/backup
 DataMemory=512M

 #Por cada nodo debe cerrar con [MYSQLD]
 [MYSQLD]
 [MYSQLD]

**Two Storage Nodes**
1.- Install Ubuntu Server Natty 11.04 with LAMP option.
2.- Install MySQL Server.
     sudo apt-get install mysql-server
3.- Install MySQL Cluster Server.
     sudo apt-get install mysql-cluster-server
4.- Configure /etc/mysql/my.cnf
I add in the last lines of file:

[mysqld]
 ndbcluster
 ndb-connectstring=192.168.1.1 #Ip de la consola de administracion

 Añadir al final del archivo
 [mysql_cluster]
 ndb-connectstring=192.168.1.1

Ok, all work fine, I probe the server and not problem.

But I don't know configure mysql-proxy to balanced charge and can not access
PHP to database.

Can you help me?...

Thanks
Best Regards

---

### Post by lisati on 2011-06-13
Not a tutorial or tip

*Thread moved to **General Help**.*

---

