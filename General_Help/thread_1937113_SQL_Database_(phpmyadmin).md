---
title: "SQL Database (phpmyadmin)"
date: 2012-03-07
forum: General Help
---

### Post by Brooksy_FC on 2012-03-07
I've got a LAMP server installed onto my machine. On phpMyAdmin, I have information_schema, mysql, phpmyadmin as a list of databases's. 

I want to create a database with some lists of names, locations and ages to test with. I then want to be able to view them on a website where a user can select a query (for example all the people in the table that at 21) and it comes back on the website with the results. 

Do I need to create a new database or use one that is already there. I'm new to SQL. Can anyone give me some help and guidance.

---

### Post by Khayyam on 2012-03-07
> **Brooksy_FC said:**
> [...]Do I need to create a new database or use one that is already there. I'm new to SQL. Can anyone give me some help and guidance.

Yes, leave the default mysql database and create a new database for each project. I don't use phpmyadmin and so I'm not going to be much help in that regard, I'm sure its a just click away.

I could show you how to do it via the command line, ask if need be ...

best ... khay

---

### Post by Brooksy_FC on 2012-03-07
> **Khayyam said:**
> Yes, leave the default mysql database and create a new database for each project. I don't use phpmyadmin and so I'm not going to be much help in that regard, I'm sure its a just click away.

I could show you how to do it via the command line, ask if need be ...


Thanks for the response. If you could that would be helpful. Just want to get an idea on what I'm doing on here :P

---

### Post by squilookle on 2012-03-07
I would also recommend something reading up on the subject. I started with one of the "For Dummies" books which was easy to read and covered PHP, and MySQL, including PHPMyAdmin, security, database design, interacting with your database using PHP scripts, and so on. 

I can give you the details of the book if you want, or have a look wherever you would normally find books, as there will be loads of others that would help too.

---

### Post by Brooksy_FC on 2012-03-07
Thanks for the suggestions. I have looked up bits and pieces and I'm understanding some of it.

**Khayyam** might be able to help me using the command line.

---

### Post by Khayyam on 2012-03-07
> **Brooksy_FC said:**
> Thanks for the response. If you could that would be helpful. Just want to get an idea on what I'm doing on here

OK ... so I have it pretty much scripted as I need to do this often for users/projects.

```
#!/bin/sh
# new-db.sh

# You can add the root mysql password here (for convenience), but keep
# this script go-rwx and under a directory not accessable to users.

ROOT_MYSQL_PASS=''

if [[ -z ${ROOT_MYSQL_PASS} ]]; then 
    echo "The ROOT_MYSQL_PASS enviroment variable is empty, either pass"
    echo "it on the command line or edit this script and add it."
    exit
fi

# The DB_ADMIN variable can be set here is incase your root mysql account is
# under a different name, otherwise it'll default to "root"

DB_ADMIN=''

if [[ (-z "$1") || (-z "$2") || (-n "$3") || ("$1" = "--help") ]]
then
    echo "    Usage: "$(basename $0)" database [password]"
    exit 0
fi

# Gather configuration
db=$(echo $1 | tr -d ' :.')

# The account password
[[ "$2" ]] && pass=$2

# setup mysql

echo "*** Setting up mysql database \"${db}\""

if [[ -d /var/lib/mysql/${db} ]] ; then
    echo "*** A database of this name already exists ... Aborting"
    exit 0
else
    
echo "Creating db with the following settings:"
echo "  - Database: ${db}"
echo "  - DB User:  ${db}"
echo "  - Password: ${pass}"
echo
echo " Ctrl-C now to abort, or press enter to continue"

read i

# Process wasn't aborted .. continue

# Do database stuff

dbsuccess=0

echo "REPLACE INTO mysql.user SET Host = 'localhost', \
User = '${db}', Password = PASSWORD('${pass}'), \
Select_priv = 'N', \
Insert_priv = 'N', \
Update_priv = 'N', \
Delete_priv = 'N', \
Create_priv = 'N', \
Drop_priv = 'N', \
Reload_priv = 'N', \
Shutdown_priv = 'N', \
Process_priv = 'N', \
File_priv = 'N', \
Grant_priv = 'N', \
References_priv = 'N', \
Index_priv = 'N', \
Alter_priv = 'N';" >| user-sql-data

echo "CREATE DATABASE IF NOT EXISTS \`${db}\`;" >> user-sql-data
echo "FLUSH PRIVILEGES;" >> user-sql-data
echo "GRANT \
Select, \
Insert, \
Update, \
Delete, \
Create, \
Drop, \
References, \
Index, \
Alter ON \`${db}\` . * TO '${db}'@'localhost';" >> user-sql-data

cat user-sql-data | mysql -u ${DB_ADMIN:-root} --password="${ROOT_MYSQL_PASS}" \
    && dbsuccess=0

rm -f user-sql-data

[[ $dbsuccess -eq 1 ]] && echo "** Database operation failed" && exit 1
[[ $dbsuccess -eq 0 ]] && echo "** Database operation succeeded"

echo "** db creation successful"

fi
```It's pretty well commented, you just to provide a "name" and "password" and run it. The "database name" will be the same as the "user". 

HTH ... khay

---

### Post by Brooksy_FC on 2012-03-07
Thanks for the code, looks a lot more than I expect haha :o I'll give it a read through.

---

### Post by Khayyam on 2012-03-07
> **Brooksy_FC said:**
> Thanks for the code, looks a lot more than I expect haha [..] I'll give it a read through.

Your welcome ... everything that is echo'ed into user-sql-data is MySQL commands, its just quicker to script, two seconds and the database is created. Note that mostly its abount granting/denying privilages, this is more 'production' oriented, but these shouldn't effect normal MySQL use, its more a matter of preventing users from abusing the main MySQL database.

best ... khay

---

### Post by Brooksy_FC on 2012-03-07
Cool, this is only going to be a test database so we have a bigger project lined up soon with large amounts of data so how would I go about deleting the test database if needs be?

---

### Post by Khayyam on 2012-03-07
> **Brooksy_FC said:**
> Cool, this is only going to be a test database so we have a bigger project lined up soon with large amounts of data so how would I go about deleting the test database if needs be?

```
mysql> drop database <name>
```

Where <name> is the name of the database ...

best ... khay

---

### Post by Brooksy_FC on 2012-03-08
> **Khayyam said:**
> ```
mysql> drop database <name>
```

Where <name> is the name of the database ...

best ... khay

Nice One! Thanks :D

---

### Post by Khayyam on 2012-03-08
> **Brooksy_FC said:**
> Nice One! Thanks

No prob ... I should have explained however that the "mysql>" is the MySQL prompt. So, you would first need to login to mysqld (the mysql service)

```
% mysql -u root -p
mysql> drop database <name>
```

best ... khay

---

### Post by Brooksy_FC on 2012-03-08
Cool, cheers. Do you know if there is another way of doing this without code?

---

### Post by Khayyam on 2012-03-08
> **Brooksy_FC said:**
> Cool, cheers. Do you know if there is another way of doing this without code?

Your looping back to your initial question ... yes, phpmyadmin, but as I said I don't use it, but I can tell you how to do it via the command line [:loop:]

best ... khay

---

