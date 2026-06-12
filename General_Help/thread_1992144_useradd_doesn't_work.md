---
title: "useradd doesn't work"
date: 2012-05-31
forum: General Help
---

### Post by H3110 on 2012-05-31
Hi Community

I have a bash script which, when executed should create one of several types of accounts. The problem is when I attemp the following:

Fail #1:
```
useradd -D -U -G srv-admin,www-data,svn -s /bin/bash -p ${PASSWORD} ${ACCOUNT}
```

FAil #2:
```
useradd -D -s /bin/bash ${ACCOUNT}
usermod -aG srv-admin,www-data,svn -p ${PASSWORD} ${ACCOUNT}
```

Fail #3:
```
adduser --quiet --disabled-password --shell /bin/bash ${ACCOUNT}
usermod -aG srv-admin,www-data,svn -p ${PASSWORD} ${ACCOUNT}
```

Is there a way of getting this to work?

---

### Post by Cheesemill on 2012-05-31
Are you using the sudo command to run your script? useradd needs to be run with root privileges.

---

### Post by H3110 on 2012-05-31
Yeah, sorry for the lack of information.

Basically I have a shell script. add_account.sh

```
sudo ./add_account.sh -t admin -a username -p password
```

Thus will eventually go to...

```
adduser ...
```

My two problem is: using adduser will prompt me for profile info such as "first name and last name" where, should i run this script by an automatic process, I don't want the script hanging for a response it wont ever receive.

So I noticed useradd would allow me to parse the user and password, and additional properties like shell, groups etc. Except thus doesn't work somehow i'm not correctly sending arguements

---

### Post by H3110 on 2012-05-31
**UPDATE**

I've made a huge mistake, forgetting about the **chpasswd** method. To this end, I have solved the problem. For anyone else seeking this solution; see below:

```
#!/bin/bash

# Some processing here...

useradd -m -G srv-admin,www-data,svn -s /bin/bash
echo "${ACCOUNT}:${PASSWORD}" | chpasswd
```

---

