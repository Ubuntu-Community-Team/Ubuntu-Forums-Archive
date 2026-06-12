---
title: "Permissions issues with daloradius/freeradius"
date: 2011-04-29
forum: General Help
---

### Post by modsbyus on 2011-04-29
Every time I try to make a change that writes to any freeradius conf file I get: **the file /etc/freeradius/****.conf isn't writable, I can't save **** information to the file** I have tried to change the permissions on the required conf files, but then freeradius complains about the files being globally writable and wont start properly. I am Really stumped here and could reallly use some help.

---

### Post by idoitprone on 2011-04-29
Changing permissions on you system files is bad. That is why chmod recurive flag is a capital R, they dont want you to acciently type it. Follow this guide [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and learn to use sudo. Only root or admins can edit those files, since they are afterall own by root, but not the user.

---

### Post by modsbyus on 2011-04-29
> **idoitprone said:**
> Changing permissions on you system files is bad. That is why chmod recurive flag is a capital R, they dont want you to acciently type it. Follow this guide [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and learn to use sudo. Only root or admins can edit those files, since they are afterall own by root, but not the user.

I am aware of that.These changes were only made to test and then the permissions were reinstated as they were originally. 
I need the application working. Not a sudoers class. Nothing you said was any help to the problem presented. 
I guess I should also mention that the changing of permissions of configuration files while building a server IS REQUIRED.

---

### Post by idoitprone on 2011-04-29
I gave you applicable information. You use sudo to edit configuration files and run the program as a normal user? 

edit: wait use chown command, this will temporary give you ownership of the file, so you will get complete control over it

chown user:group filename

of course use sudo to use the chown command, then change it back

---

### Post by modsbyus on 2011-04-29
> **idoitprone said:**
> I gave you applicable information. You use sudo to edit configuration files and run the program as a normal user? 

edit: wait use chown command

chown user:group filename

of course use sudo, then change it back

How has this helped me. You haven't taught me anything new.
I have a web based management interface that is suppose to be able to actively make changes to configuration files in freeradius and it wont do it. TEMPORARILY changing the files' permissions allowed me to test. I need help with what I am suppose to change. Is what I am suppose to change in the conf files for daloradius or the ownership of freeradius files???

---

### Post by idoitprone on 2011-04-29
I am sorry. I am a confusing person to understand. What I am advocating is change the owner of a file. The trick that you made it work is that you allow  others to write. I believe the program hates that.
You know linux permission right?
Then you know that ls -l  list them as owner,group,others

What I am advocating is that I want you to change the owner to an user of your choice this way, you can edit those file without sudo or give full permissions to anyone

---

### Post by modsbyus on 2011-04-29
> **idoitprone said:**
> I am sorry. I am a confusing person to understand. What I am advocating is change the owner of a file. The trick that you made it work is that you allow  others to write. I believe the program hates that.
You know linux permission right?
Then you know that ls -l  list them as owner,group,others

What I am advocating is that I want you to change the owner to an user of your choice this way, you can edit those file without sudo or give full permissions to anyone

Thank you. I do understand how to change permissions and ownerships. What I didn't understand what that I could do that w/o messing something up.
Thank you again.

---

### Post by idoitprone on 2011-04-29
Dawm it I was hoping you call me an idoit, so i can make a joke once.

Rant: the only reason why I learn permission to this point. Screw arch. One time i made an account and it didnt make a home directory. made me do all the work changing permission copying from /etc/skel and etc

```
chown username filename
``` only the owner is changed

```
chmod 700 filename
```

only the user has full permissions

gtg I have to do errands bye

---

### Post by modsbyus on 2011-04-29
OK, I have changed the owners of the files to my user for freeradius and daloradius. I have permissions to read and write the files. However, daloradius still can't write to the .conf files. Shouldn't changing the owner and group to the same owner and group as freeradius give it the same writing privileges??

---

### Post by idoitprone on 2011-04-29
```
ls -l
``` the conf file and post the output here. I kidda want to see the permission on the file

the program should be able to write to the file, if it is properly changed

---

### Post by modsbyus on 2011-04-29
> **idoitprone said:**
> ```
ls -l
``` the conf file and post the output here. I kidda want to see the permission on the file

the program should be able to write to the file, if it is properly changed

When i run ls -l in the directories it returns that i am the owner and group.

---

### Post by idoitprone on 2011-04-29
no i wanted to see the like -rwx------. Those should be the permission to the file. If it is, then i cannot help you since I do not understand what is wrong.

reading material [http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

---

### Post by modsbyus on 2011-04-29
```
gary@freeradius01:/var/www/daloradius$ ls -l
total 1612
-rwxrwxr-x 1 gary gary  8908 2009-01-27 12:46 acct-active.php
-rwxrwxr-x 1 gary gary 10588 2009-01-27 12:46 acct-all.php
-rwxrwxr-x 1 gary gary  1706 2009-01-27 12:46 acct-custom.php
-rwxrwxr-x 1 gary gary  6505 2009-01-27 12:46 acct-custom-query.php
-rwxrwxr-x 1 gary gary 12969 2009-01-27 12:46 acct-date.php
-rwxrwxr-x 1 gary gary 10623 2009-01-27 12:46 acct-hotspot-accounting.php
-rwxrwxr-x 1 gary gary  5668 2009-01-27 12:46 acct-hotspot-compare.php
-rwxrwxr-x 1 gary gary  1687 2009-01-27 12:46 acct-hotspot.php
-rwxrwxr-x 1 gary gary 11607 2009-01-27 12:46 acct-ipaddress.php
-rwxrwxr-x 1 gary gary  1680 2009-01-27 12:46 acct-main.php
-rwxrwxr-x 1 gary gary  4361 2009-01-27 12:46 acct-maintenance-cleanup.php
-rwxrwxr-x 1 gary gary  5460 2009-01-27 12:46 acct-maintenance-delete.php
-rwxrwxr-x 1 gary gary  1697 2009-01-27 12:46 acct-maintenance.php
-rwxrwxr-x 1 gary gary 11836 2009-01-27 12:46 acct-nasipaddress.php
-rwxrwxr-x 1 gary gary 10608 2009-01-27 12:46 acct-username.php
-rwxrwxr-x 1 gary gary   919 2009-01-27 12:46 bill-history.php
-rwxrwxr-x 1 gary gary  8254 2009-01-27 12:46 bill-history-query.php
-rwxrwxr-x 1 gary gary   910 2009-01-27 12:46 bill-main.php
-rwxrwxr-x 1 gary gary   915 2009-01-27 12:46 bill-paypal.php
-rwxrwxr-x 1 gary gary  9619 2009-01-27 12:46 bill-paypal-transactions.php
-rwxrwxr-x 1 gary gary  4389 2009-01-27 12:46 bill-plans-del.php
-rwxrwxr-x 1 gary gary 25551 2009-01-27 12:46 bill-plans-edit.php
-rwxrwxr-x 1 gary gary  7223 2009-01-27 12:46 bill-plans-list.php
-rwxrwxr-x 1 gary gary 20228 2009-01-27 12:46 bill-plans-new.php
-rwxrwxr-x 1 gary gary   898 2009-01-27 12:46 bill-plans.php
-rwxrwxr-x 1 gary gary  8768 2009-01-27 12:46 bill-pos-del.php
-rwxrwxr-x 1 gary gary 36924 2009-01-27 12:46 bill-pos-edit.php
-rwxrwxr-x 1 gary gary 10584 2009-01-27 12:46 bill-pos-list.php
-rwxrwxr-x 1 gary gary 27146 2009-01-27 12:46 bill-pos-new.php
-rwxrwxr-x 1 gary gary   894 2009-01-27 12:46 bill-pos.php
-rwxrwxr-x 1 gary gary  5645 2009-01-27 12:46 bill-prepaid.php
-rwxrwxr-x 1 gary gary  9555 2009-01-27 12:46 bill-rates-date.php
-rwxrwxr-x 1 gary gary  3937 2009-01-27 12:46 bill-rates-del.php
-rwxrwxr-x 1 gary gary  8869 2009-01-27 12:46 bill-rates-edit.php
-rwxrwxr-x 1 gary gary  7430 2009-01-27 12:46 bill-rates-list.php
-rwxrwxr-x 1 gary gary  8638 2009-01-27 12:46 bill-rates-new.php
-rwxrwxr-x 1 gary gary   913 2009-01-27 12:46 bill-rates.php
-rwxrwxr-x 1 gary gary 19128 2009-01-27 12:50 ChangeLog
-rwxrwxr-x 1 gary gary 15717 2009-01-27 12:46 config-backup-createbackups.php
-rwxrwxr-x 1 gary gary  6851 2009-01-27 12:46 config-backup-managebackups.php
-rwxrwxr-x 1 gary gary  1723 2009-01-27 12:46 config-backup.php
-rwxrwxr-x 1 gary gary 14442 2009-01-27 12:46 config-db.php
-rwxrwxr-x 1 gary gary  4869 2009-01-27 12:46 config-interface.php
-rwxrwxr-x 1 gary gary  2981 2009-01-27 12:46 config-lang.php
-rwxrwxr-x 1 gary gary  5836 2009-01-27 12:46 config-logging.php
-rwxrwxr-x 1 gary gary  1692 2009-01-27 12:46 config-main.php
-rwxrwxr-x 1 gary gary  9350 2009-01-27 12:46 config-maint-disconnect-user.php
-rwxrwxr-x 1 gary gary  1719 2009-01-27 12:46 config-maint.php
-rwxrwxr-x 1 gary gary  8691 2009-01-27 12:46 config-maint-test-user.php
-rwxrwxr-x 1 gary gary  4118 2009-01-27 12:46 config-operators-del.php
-rwxrwxr-x 1 gary gary  6700 2009-01-27 12:46 config-operators-edit.php
-rwxrwxr-x 1 gary gary  8005 2009-01-27 12:46 config-operators-list.php
-rwxrwxr-x 1 gary gary  7046 2009-01-27 12:46 config-operators-new.php
-rwxrwxr-x 1 gary gary  1795 2009-01-27 12:46 config-operators.php
drwxrwxr-x 5 gary gary  4096 2009-01-27 12:50 contrib
drwxrwxr-x 2 gary gary  4096 2009-01-27 12:50 css
drwxrwxr-x 7 gary gary  4096 2009-01-27 12:50 daloradius-users
-rwxrwxr-x 1 gary gary  3544 2009-01-27 12:46 dologin.php
-rwxrwxr-x 1 gary gary  1428 2009-01-27 12:46 FAQS
-rwxrwxr-x 1 gary gary  5175 2009-01-27 12:46 gis-editmap.php
-rwxrwxr-x 1 gary gary  1457 2009-01-27 12:46 gis-main.php
-rwxrwxr-x 1 gary gary  4251 2009-01-27 12:46 gis-viewmap.php
-rwxrwxr-x 1 gary gary   725 2009-01-27 12:46 graph-main.php
-rwxrwxr-x 1 gary gary  1599 2009-01-27 12:46 graphs-alltime_logins.php
-rwxrwxr-x 1 gary gary  1377 2009-01-27 12:46 graphs-alltime_traffic_compare.php
-rwxrwxr-x 1 gary gary  1699 2009-01-27 12:46 graphs-overall_download.php
-rwxrwxr-x 1 gary gary  1665 2009-01-27 12:46 graphs-overall_logins.php
-rwxrwxr-x 1 gary gary  1673 2009-01-27 12:46 graphs-overall_upload.php
-rwxrwxr-x 1 gary gary  1099 2009-01-27 12:46 help-main.php
drwxrwxr-x 3 gary gary  4096 2009-01-27 12:50 images
drwxrwxr-x 6 gary gary  4096 2009-01-27 12:50 include
-rwxrwxr-x 1 gary gary   529 2009-01-27 12:46 index.php
-rwxrwxr-x 1 gary gary  7774 2009-01-27 12:46 INSTALL
-rwxrwxr-x 1 gary gary  7274 2009-01-27 12:46 INSTALL.openSUSE
-rwxrwxr-x 1 gary gary  2689 2009-01-27 12:46 INSTALL.quick
-rwxrwxr-x 1 gary gary  2423 2009-01-27 12:46 INSTALL.win
drwxrwxr-x 2 gary gary  4096 2009-01-27 12:50 lang
drwxrwxr-x 6 gary gary  4096 2011-04-28 11:53 library
-rwxrwxr-x 1 gary gary 18011 2009-01-27 12:46 LICENSE
-rwxrwxr-x 1 gary gary  2634 2009-01-27 12:46 login.php
-rwxrwxr-x 1 gary gary   334 2009-01-27 12:46 logout.php
-rwxrwxr-x 1 gary gary 10202 2009-01-27 12:46 menu-accounting-custom.php
-rwxrwxr-x 1 gary gary  2392 2009-01-27 12:46 menu-accounting-hotspot.php
-rwxrwxr-x 1 gary gary  1478 2009-01-27 12:46 menu-accounting-maintenance.php
-rwxrwxr-x 1 gary gary  6268 2009-01-27 12:46 menu-accounting.php
-rwxrwxr-x 1 gary gary  8211 2009-01-27 12:46 menu-bill-history.php
-rwxrwxr-x 1 gary gary  5200 2009-01-27 12:46 menu-billing.php
-rwxrwxr-x 1 gary gary 10829 2009-01-27 12:46 menu-bill-paypal.php
-rwxrwxr-x 1 gary gary  2339 2009-01-27 12:46 menu-bill-plans.php
-rwxrwxr-x 1 gary gary  2419 2009-01-27 12:46 menu-bill-pos.php
-rwxrwxr-x 1 gary gary  6349 2009-01-27 12:46 menu-bill-rates.php
-rwxrwxr-x 1 gary gary  1163 2009-01-27 12:46 menu-config-backup.php
-rwxrwxr-x 1 gary gary  1176 2009-01-27 12:46 menu-config-maint.php
-rwxrwxr-x 1 gary gary  2145 2009-01-27 12:46 menu-config-operators.php
-rwxrwxr-x 1 gary gary  1218 2009-01-27 12:46 menu-config.php
-rwxrwxr-x 1 gary gary  1522 2009-01-27 12:46 menu-gis.php
-rwxrwxr-x 1 gary gary  5858 2009-01-27 12:46 menu-graphs.php
-rwxrwxr-x 1 gary gary   441 2009-01-27 12:46 menu-help.php
-rwxrwxr-x 1 gary gary  1478 2009-01-27 12:46 menu-home.php
-rwxrwxr-x 1 gary gary  2246 2009-01-27 12:46 menu-mng-hs.php
-rwxrwxr-x 1 gary gary  4327 2009-01-27 12:46 menu-mng-rad-attributes.php
-rwxrwxr-x 1 gary gary  4730 2009-01-27 12:46 menu-mng-rad-groups.php
-rwxrwxr-x 1 gary gary  2059 2009-01-27 12:46 menu-mng-rad-ippool.php
-rwxrwxr-x 1 gary gary  2226 2009-01-27 12:46 menu-mng-rad-nas.php
-rwxrwxr-x 1 gary gary  1455 2009-01-27 12:46 menu-mng-rad-profiles.php
-rwxrwxr-x 1 gary gary  1701 2009-01-27 12:46 menu-mng-rad-realms.php
-rwxrwxr-x 1 gary gary  3489 2009-01-27 12:46 menu-mng-rad-usergroup.php
-rwxrwxr-x 1 gary gary  3578 2009-01-27 12:46 menu-mng-users.php
-rwxrwxr-x 1 gary gary  8215 2009-01-27 12:46 menu-reports-logs.php
-rwxrwxr-x 1 gary gary  4816 2009-01-27 12:46 menu-reports.php
-rwxrwxr-x 1 gary gary  1208 2009-01-27 12:46 menu-reports-status.php
-rwxrwxr-x 1 gary gary 13244 2009-01-27 12:46 mng-batch.php
-rwxrwxr-x 1 gary gary  8526 2009-01-27 12:46 mng-del.php
-rwxrwxr-x 1 gary gary 38876 2009-02-07 11:41 mng-edit.php
-rwxrwxr-x 1 gary gary  4370 2009-01-27 12:46 mng-hs-del.php
-rwxrwxr-x 1 gary gary  8556 2009-01-27 12:46 mng-hs-edit.php
-rwxrwxr-x 1 gary gary  8254 2009-01-27 12:46 mng-hs-list.php
-rwxrwxr-x 1 gary gary  8203 2009-01-27 12:46 mng-hs-new.php
-rwxrwxr-x 1 gary gary   907 2009-01-27 12:46 mng-hs.php
-rwxrwxr-x 1 gary gary 10252 2009-02-07 11:39 mng-list-all.php
-rwxrwxr-x 1 gary gary  1023 2009-01-27 12:46 mng-main.php
-rwxrwxr-x 1 gary gary 28962 2009-01-27 12:46 mng-new.php
-rwxrwxr-x 1 gary gary 21615 2009-01-27 12:46 mng-new-quick.php
-rwxrwxr-x 1 gary gary  6228 2009-01-27 12:46 mng-rad-attributes-del.php
-rwxrwxr-x 1 gary gary 11405 2009-01-27 12:46 mng-rad-attributes-edit.php
-rwxrwxr-x 1 gary gary  7287 2009-01-27 12:46 mng-rad-attributes-import.php
-rwxrwxr-x 1 gary gary  8003 2009-01-27 12:46 mng-rad-attributes-list.php
-rwxrwxr-x 1 gary gary  8545 2009-01-27 12:46 mng-rad-attributes-new.php
-rwxrwxr-x 1 gary gary  2136 2009-01-27 12:46 mng-rad-attributes.php
-rwxrwxr-x 1 gary gary  7481 2009-01-27 12:46 mng-rad-attributes-search.php
-rwxrwxr-x 1 gary gary  6252 2009-01-27 12:46 mng-rad-groupcheck-del.php
-rwxrwxr-x 1 gary gary  6558 2009-01-27 12:46 mng-rad-groupcheck-edit.php
-rwxrwxr-x 1 gary gary  6299 2009-01-27 12:46 mng-rad-groupcheck-list.php
-rwxrwxr-x 1 gary gary  6730 2009-01-27 12:46 mng-rad-groupcheck-new.php
-rwxrwxr-x 1 gary gary  6037 2009-01-27 12:46 mng-rad-groupcheck-search.php
-rwxrwxr-x 1 gary gary  5543 2009-01-27 12:46 mng-rad-groupreply-del.php
-rwxrwxr-x 1 gary gary  6595 2009-01-27 12:46 mng-rad-groupreply-edit.php
-rwxrwxr-x 1 gary gary  6314 2009-01-27 12:46 mng-rad-groupreply-list.php
-rwxrwxr-x 1 gary gary  6619 2009-01-27 12:46 mng-rad-groupreply-new.php
-rwxrwxr-x 1 gary gary  6064 2009-01-27 12:46 mng-rad-groupreply-search.php
-rwxrwxr-x 1 gary gary  2126 2009-01-27 12:46 mng-rad-groups.php
-rwxrwxr-x 1 gary gary  4905 2009-01-27 12:46 mng-rad-ippool-del.php
-rwxrwxr-x 1 gary gary  5526 2009-01-27 12:46 mng-rad-ippool-edit.php
-rwxrwxr-x 1 gary gary  7533 2009-01-27 12:46 mng-rad-ippool-list.php
-rwxrwxr-x 1 gary gary  4784 2009-01-27 12:46 mng-rad-ippool-new.php
-rwxrwxr-x 1 gary gary  2126 2009-01-27 12:46 mng-rad-ippool.php
-rwxrwxr-x 1 gary gary  4750 2009-01-27 12:46 mng-rad-nas-del.php
-rwxrwxr-x 1 gary gary  9358 2009-01-27 12:46 mng-rad-nas-edit.php
-rwxrwxr-x 1 gary gary  7996 2009-01-27 12:46 mng-rad-nas-list.php
-rwxrwxr-x 1 gary gary  7524 2009-01-27 12:46 mng-rad-nas-new.php
-rwxrwxr-x 1 gary gary  2134 2009-01-27 12:46 mng-rad-nas.php
-rwxrwxr-x 1 gary gary  5877 2009-01-27 12:46 mng-rad-profiles-del.php
-rwxrwxr-x 1 gary gary  5600 2009-01-27 12:46 mng-rad-profiles-duplicate.php
-rwxrwxr-x 1 gary gary 15836 2009-01-27 12:46 mng-rad-profiles-edit.php
-rwxrwxr-x 1 gary gary  7599 2009-01-27 12:46 mng-rad-profiles-list.php
-rwxrwxr-x 1 gary gary  5203 2009-01-27 12:46 mng-rad-profiles-new.php
-rwxrwxr-x 1 gary gary  2136 2009-01-27 12:46 mng-rad-profiles.php
-rwxrwxr-x 1 gary gary  4433 2009-01-27 12:46 mng-rad-proxys-del.php
-rwxrwxr-x 1 gary gary  9810 2009-01-27 12:46 mng-rad-proxys-edit.php
-rwxrwxr-x 1 gary gary  5556 2009-01-27 12:46 mng-rad-proxys-list.php
-rwxrwxr-x 1 gary gary  8619 2009-01-27 12:46 mng-rad-proxys-new.php
-rwxrwxr-x 1 gary gary  4451 2009-01-27 12:46 mng-rad-realms-del.php
-rwxrwxr-x 1 gary gary 12259 2009-01-27 12:46 mng-rad-realms-edit.php
-rwxrwxr-x 1 gary gary  5544 2009-01-27 12:46 mng-rad-realms-list.php
-rwxrwxr-x 1 gary gary 11316 2009-01-27 12:46 mng-rad-realms-new.php
-rwxrwxr-x 1 gary gary  2133 2009-01-27 12:46 mng-rad-realms.php
-rwxrwxr-x 1 gary gary  5828 2009-01-27 12:46 mng-rad-usergroup-del.php
-rwxrwxr-x 1 gary gary  7636 2009-01-27 12:46 mng-rad-usergroup-edit.php
-rwxrwxr-x 1 gary gary  7517 2009-01-27 12:46 mng-rad-usergroup-list.php
-rwxrwxr-x 1 gary gary  5607 2009-01-27 12:46 mng-rad-usergroup-list-user.php
-rwxrwxr-x 1 gary gary  5699 2009-01-27 12:46 mng-rad-usergroup-new.php
-rwxrwxr-x 1 gary gary  2136 2009-01-27 12:46 mng-rad-usergroup.php
-rwxrwxr-x 1 gary gary  7837 2009-01-27 12:46 mng-search.php
-rwxrwxr-x 1 gary gary  1937 2009-01-27 12:46 mng-users.php
-rwxrwxr-x 1 gary gary  2003 2009-01-27 12:46 msg-error-permissions.php
-rwxrwxr-x 1 gary gary  1030 2009-01-27 12:46 page-footer.php
-rwxrwxr-x 1 gary gary  7607 2009-01-27 12:46 README
-rwxrwxr-x 1 gary gary  6906 2009-01-27 12:46 rep-history.php
-rwxrwxr-x 1 gary gary  7720 2009-01-27 12:46 rep-lastconnect.php
-rwxrwxr-x 1 gary gary  2329 2009-01-27 12:46 rep-logs-boot.php
-rwxrwxr-x 1 gary gary  2330 2009-01-27 12:46 rep-logs-daloradius.php
-rwxrwxr-x 1 gary gary  1682 2009-01-27 12:46 rep-logs.php
-rwxrwxr-x 1 gary gary  2251 2009-01-27 12:46 rep-logs-radius.php
-rwxrwxr-x 1 gary gary  2359 2009-01-27 12:46 rep-logs-system.php
-rwxrwxr-x 1 gary gary  1666 2009-01-27 12:46 rep-main.php
-rwxrwxr-x 1 gary gary  9313 2009-01-27 12:46 rep-online.php
-rwxrwxr-x 1 gary gary  1831 2009-01-27 12:46 rep-stat-server.php
-rwxrwxr-x 1 gary gary  1839 2009-01-27 12:46 rep-stat-services.php
-rwxrwxr-x 1 gary gary  1692 2009-01-27 12:46 rep-status.php
-rwxrwxr-x 1 gary gary  5510 2009-01-27 12:46 rep-topusers.php
-rwxrwxr-x 1 gary gary  7410 2009-01-27 12:46 rep-username.php
-rwxrwxr-x 1 gary gary 44305 2009-01-27 12:46 update.php
drwxrwxr-x 3 gary gary  4096 2009-01-27 12:50 var
gary@freeradius01:/var/www/daloradius$
```

```
gary@freeradius01:/etc/freeradius$ ls -l
total 224
-rwxrwxr-x 1 gary gary   671 2009-04-30 03:23 acct_users
-rwxrwxr-x 1 gary gary  4174 2009-04-30 03:23 attrs
-rwxrwxr-x 1 gary gary   458 2009-04-30 03:23 attrs.access_reject
-rwxrwxr-x 1 gary gary   437 2009-04-30 03:23 attrs.accounting_response
-rwxrwxr-x 1 gary gary  2022 2009-04-30 03:23 attrs.pre-proxy
drwxrwsr-x 2 gary gary  4096 2009-04-30 03:23 certs
-rwxrwxr-x 1 gary gary  6462 2009-04-30 03:23 clients.conf
-rwxrwxr-x 1 gary gary   877 2009-04-30 03:23 dictionary
-rwxrwxr-x 1 gary gary 14928 2011-04-29 09:01 eap.conf
-rwxrwxr-x 1 gary gary 14927 2011-04-28 12:50 eap.conf~
-rwxrwxr-x 1 gary gary 14479 2009-04-30 03:23 experimental.conf
-rwxrwxr-x 1 gary gary  2352 2009-04-30 03:23 hints
-rwxrwxr-x 1 gary gary  1604 2009-04-30 03:23 huntgroups
-rwxrwxr-x 1 gary gary  3017 2009-04-30 03:23 ldap.attrmap
drwxrwxr-x 2 gary gary  4096 2011-04-26 11:56 modules
-rwxrwxr-x 1 gary gary  3357 2009-04-30 03:23 otp.conf
-rwxrwxr-x 1 gary gary  1154 2009-04-30 03:23 policy.conf
-rwxrwxr-x 1 gary gary  4873 2009-04-30 03:23 policy.txt
-rwxrwxr-x 1 gary gary   984 2009-04-30 03:23 preproxy_users
-rwxrwxr-x 1 gary gary    81 2011-04-29 13:53 proxy.conf
-rwxrwxr-x 1 gary gary    82 2011-04-28 12:38 proxy.conf~
-rwxrwxr-x 1 gary gary 25594 2011-04-29 13:57 radiusd.conf
-rwxrwxr-x 1 gary gary 25661 2011-04-29 11:46 radiusd.conf~
drwxrwsr-x 2 gary gary  4096 2011-04-26 11:56 sites-available
drwxrwsr-x 2 gary gary  4096 2011-04-26 11:56 sites-enabled
drwxrwsr-x 3 gary gary  4096 2011-04-26 11:56 sql
-rwxrwxr-x 1 gary gary  2485 2011-04-26 15:25 sql.conf
-rwxrwxr-x 1 gary gary  2485 2009-04-30 03:23 sql.conf~
-rwxrwxr-x 1 gary gary  1933 2009-04-30 03:23 sqlippool.conf
-rwxrwxr-x 1 gary gary  3450 2009-04-30 03:23 templates.conf
-rwxrwxr-x 1 gary gary  6524 2009-04-30 03:23 users
gary@freeradius01:/etc/freeradius$
```

---

### Post by idoitprone on 2011-04-29
i cant really help the permission seems correct, since you are running the program as gary? Are you not? It should work.

---

### Post by modsbyus on 2011-04-29
I'm not sure who the program starts under. its a service that starts with the computer. how would I check that?

---

### Post by idoitprone on 2011-04-29
```
whoami
``` check which user is running at the moment


In most cases, you dont need a command
```

[SIZE=4]**gary**[/SIZE]@freeradius01:/var/www/daloradius$ ls -l
total 1612
-rwxrwxr-x 1 gary gary  8908 2009-01-27 12:46 acct-active.php
-rwxrwxr-x 1 gary gary 10588 2009-01-27 12:46 acct-all.php
-rwxrwxr-x 1 gary gary  1706 2009-01-27 12:46 acct-custom.php
-rwxrwxr-x 1 gary gary  6505 2009-01-27 12:46 acct-custom-query.php
-rwxrwxr-x 1 gary gary 12969 2009-01-27 12:46 acct-date.php
-rwxrwxr-x 1 gary gary 10623 2009-01-27 12:46 acct-hotspot-counting.php 
``````
ps -ef | grep command 
```see which user is running the command

---

### Post by modsbyus on 2011-04-29
> **idoitprone said:**
> ```
whoami
``` check which user is running at the moment


In most cases, you dont need a command
```

[SIZE=4]**gary**[/SIZE]@freeradius01:/var/www/daloradius$ ls -l
total 1612
-rwxrwxr-x 1 gary gary  8908 2009-01-27 12:46 acct-active.php
-rwxrwxr-x 1 gary gary 10588 2009-01-27 12:46 acct-all.php
-rwxrwxr-x 1 gary gary  1706 2009-01-27 12:46 acct-custom.php
-rwxrwxr-x 1 gary gary  6505 2009-01-27 12:46 acct-custom-query.php
-rwxrwxr-x 1 gary gary 12969 2009-01-27 12:46 acct-date.php
-rwxrwxr-x 1 gary gary 10623 2009-01-27 12:46 acct-hotspot-counting.php 
```

hmmmmm. well I'm logged in as gary so of course when I say whoami.. its says gary... 
So, we can agree that this is an odd issue?
```
sudo rm os
```

---

### Post by idoitprone on 2011-04-29
So you cant run it as gary?

---

### Post by modsbyus on 2011-04-29
yes

---

### Post by idoitprone on 2011-04-29
nevermind i do not understand your problem at all [https://help.ubuntu.com/community/CategoryNetworking/daloRADIUS#Setting%20Permissions]("https://help.ubuntu.com/community/CategoryNetworking/daloRADIUS#Setting%20Permissions")

I was under the assumption to just change the permissions. Sorry, i misunderstood. I realize you wanted to set it up the database. It seem like you did not completely do all the task in the wiki.

---

### Post by modsbyus on 2011-04-29
> **idoitprone said:**
> Oh, now I starting understand what you are saying. You want to run this program from start up. Judging from you previous remarks, this program is meant to be run from start up. It prob meant to be run as a daemon which mean it does not require user input. If you set it at /etc/init.d/ the program will run as root. There a way to set up. I kidda forgot how to do it for ubuntu. It differs between distro.

Well, I'm not going to modify things that much. This is intended to run with out all of this. Unfortunately the devs at daloradius aren't answering on their forums. thats why I posted here. I haven't seen in any posts any where else of people having this issue. so I guess I'll just have to wipe reload and continue the self punishment.

---

### Post by idoitprone on 2011-04-29
> **modsbyus said:**
> Well, I'm not going to modify things that much. This is intended to run with out all of this. Unfortunately the devs at daloradius aren't answering on their forums. thats why I posted here. I haven't seen in any posts any where else of people having this issue. so I guess I'll just have to wipe reload and continue the self punishment.

wait i changed my post look back

---

### Post by modsbyus on 2011-04-29
> **idoitprone said:**
> nevermind i do not understand your problem at all [https://help.ubuntu.com/community/CategoryNetworking/daloRADIUS#Setting%20Permissions]("https://help.ubuntu.com/community/CategoryNetworking/daloRADIUS#Setting%20Permissions")

I was under the assumption to just change the permissions. Sorry, i misunderstood. I realize you wanted to set it up the database. It seem like you did not completely do all the task in the wiki.

No, I followed that precisely. And before I started this thread had checked all that. I have read and write for sql in daloradius. just not to the files for freeradius. [IMG]http://www.modsbyus.com/images/radius_ss.bmp[/IMG]

---

### Post by idoitprone on 2011-04-29
```
cat /etc/groups
```wait never mind i  do not have much experience set up database ask someelse for help. The thing i can think of is adding your self to the group to the www-data group so you will gain all the permission required. return the owner and group to the guide

---

### Post by modsbyus on 2011-05-02
> **idoitprone said:**
> ```
cat /etc/groups
```wait never mind i  do not have much experience set up database ask someelse for help. The thing i can think of is adding your self to the group to the www-data group so you will gain all the permission required. return the owner and group to the guide

I don't see a www-data group. Could that be the issue? Apache2 is installed.

---

### Post by idoitprone on 2011-05-03
Probably, you should ask someone else about setting up the server. If you set the group as a nonexisting group, it should be no different as setting as root. I believe the permission problem stem from that. Like I said, I am idoit. lol

---

