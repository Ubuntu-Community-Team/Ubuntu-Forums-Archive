---
title: "Script to create user, directories and site in apache"
date: 2011-05-24
forum: General Help
---

### Post by jijarine on 2011-05-24
First off, Ubuntu 10.10

I've had a recent idea to have PHP take information from a form, save it to a file, which in turn is read from a local script as root (cron) which will create the user account, proper directories, add the website to the Apache sites, and reload Apache. Has anyone actually accomplished this before? And if so, can I get some links or some ideas to possibly help me on the process of getting started?

Appreciate any input or ideas on this, as well as links, etc. I've googled myself to death looking at possibilities, but none really seem to encompase the whole scope of what I'm trying to accomplish here...

---

### Post by jijarine on 2011-05-25
So, after fiddling around I've got a decent start, figured I would share what I've go thus far.

The below code checks if a user exists, in PHP I do the following:

[PHP]
exec('/LOCATION_OF_FILE/checkuser "'.$username.'"', $results);
if (!empty($results[0])) {
  $error .= 'Username already exists, please choose another.';
}
[/PHP]checkuser
```

#!/bin/sh

if id $1 > /dev/null 2>&1
then
  echo "found"
else
  exit
fi

```I've also written a script to be executed in a cron job, this script so far will create the user, the password for said user, and the appropriate directories, etc

```

#!/bin/sh
name=$1
username=$2
password=$3
domain=$4

useradd -c "$name" -m -p $password $username
mkdir /home/$username/public_html
mkdir /home/$username/public_html/$domain
mkdir /home/$username/public_html/$domain/logs/
chgrp -R $username /home/$username/

```So now I am left with reading the CSV file, creating the appropriate files in Apache sites, creating the appropriate A records, etc. Thats where I am now stuck. Any suggestions? I will continue to Google and post if I come up with anything new.

Comments and suggestions welcome.

---

