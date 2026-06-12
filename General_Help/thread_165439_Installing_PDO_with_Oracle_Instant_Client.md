---
title: "Installing PDO with Oracle Instant Client"
date: 2006-04-24
forum: General Help
---

### Post by fsecwgb on 2006-04-24
I have Breezy Badger and I have installed Apache 2 and PHP5 and was able to get the Oracle Instant Client installed with the help of this excellent tutorial:

[http://ubuntuforums.org/showthread.php?t=92528&highlight=install+oci8](http://ubuntuforums.org/showthread.php?t=92528&highlight=install+oci8)

I am now trying to install pdo and pdo_oci.  I was able to successfully install pdo using "sudo pear install pecl/pdo"  I then edited the php.ini as in the tutorial above to add the pdo.so the list of extensions.  PDO now shows up under phpinfo().  pdo_oci however does not work.  i tried to install it using 

"sudo pear install pecl/pdo_oci"  and it bombed with 

checking Oracle OCI support for PDO... yes, shared
checking Oracle Install-Dir... /opt/oracle/instantclient :yes:
checking if that is sane... yes
checking Oracle version... configure: error: Oracle-OCI needed libraries not found under /opt/oracle/instantclient
ERROR: `/tmp/tmpezvEwk/PDO_OCI-1.0/configure' failed

All of the Oracle Instant Client install is in this directory and my oracle_home references this location.  What is it exactly that pdo_oci wants that the oracle instant client does not have.

Thanks,

Jeremiah Campbell

---

