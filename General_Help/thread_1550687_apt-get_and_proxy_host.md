---
title: "apt-get and proxy host"
date: 2010-08-11
forum: General Help
---

### Post by uttam2707 on 2010-08-11
how to configure apt-get such that it will ask for authentication (user name and password) each time while accessing the Internet via proxy host, somewhat like sudo command. I don't want my username and password to be saved by apt-get in the apt-get configuration file.

---

### Post by anglican on 2010-08-11
> **uttam2707 said:**
> how to configure apt-get such that it will ask for authentication (user name and password) each time while accessing the Internet via proxy host, somewhat like sudo command. I don't want my username and password to be saved by apt-get in the apt-get configuration file.
I can't give a direct answer to this, but I'd use (from a couple of years back) the following script which is reasonably safe (I think):
```
#!/bin/bash
echo -n "Proxy password: ";
read -es password;
echo;
export http_proxy="http://user_name:$password@proxy:port/";

if !(sudo apt-get update)
   then echo "Failure: apt-get update";
fi

sleep 2

echo -n "Run 'apt-get upgrade'? (Y/N): ";
read -e response;

if [ "$response" = "Y" ] || [ "$response" = "y" ]
   then
      if !(sudo apt-get upgrade)
         then echo "Failure: apt-get upgrade";
      fi
elif [ "$response" != "N" ] || [ "$response" != "n" ]
   then echo "$response: Invalid input.";
fi

unset http_proxy;

exit 0;
```H

---

### Post by uttam2707 on 2010-08-19
> **anglican said:**
> I can't give a direct answer to this, but I'd use (from a couple of years back) the following script which is reasonably safe (I think):
```
#!/bin/bash
echo -n "Proxy password: ";
read -es password;
echo;
export http_proxy="http://user_name:$password@proxy:port/";

if !(sudo apt-get update)
   then echo "Failure: apt-get update";
fi

sleep 2

echo -n "Run 'apt-get upgrade'? (Y/N): ";
read -e response;

if [ "$response" = "Y" ] || [ "$response" = "y" ]
   then
      if !(sudo apt-get upgrade)
         then echo "Failure: apt-get upgrade";
      fi
elif [ "$response" != "N" ] || [ "$response" != "n" ]
   then echo "$response: Invalid input.";
fi

unset http_proxy;

exit 0;
```H
Thank you very much. Can you please tell me how to use the script...rather how to use a script? actually I am not a techie.

---

