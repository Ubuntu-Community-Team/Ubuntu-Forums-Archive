---
title: "SVN checkingout"
date: 2011-06-23
forum: General Help
---

### Post by H3110 on 2011-06-23
Good Afternoon,

I have a process where by all SVN repositories are held in **/var/svn/[domain]**. I have set-up a post-commit hook to automatically checkout the repository to the development site and delete all .svn directories recursively through-out.

I intend to run a bash script (as below); this is where my problem lies. EVERY repository is "Open" and anyone can read, write and commit the repository, however thus is secure via HTTP Authentication, using **htpasswd**.

Because the hook is automatic, I would like to be able to collect the current user/password but I don't think it's possible so I have created an account for the system called "svnroot" with a password.

How can i _**authenticate**_ through the HTTP Authentication via my _**bash**_ script?

```
sudo sv_checkout -s mysite.com
```

```
#!/bin/bash -x
# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
# Checkout repository
# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

usage()
{
cat << EOF
usage: $0 options

This script will checkout a repository to development.

OPTIONS:
   -s   The site/repository.
   -u   The user checking out.
   -p   Theuser password.
EOF
}

if [ "$1" == "?" ]; then
        usage
        exit
fi

# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

SH_DIR_DEV="/var/www/"

# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

USER_NAME="svnroot"
USER_PWD="r%7P4$5w0Rd!"

while getopts ":s:up" OPT; do
        case ${OPT} in
                s) DOMAIN_NAME=${OPTARG} ;;
                u) USER_NAME=${OPTARG} ;;
                p) USER_PWD=${OPTARG} ;;
                *)
                        echo "Invalid option: -${OPT} ${OPTARG}"
                        exit 1
                ;;
        esac
done

if [[ -z "${DOMAIN_NAME}" ]] || [[ -z "${USER_NAME}" ]] || [[ -z "${USER_PWD}" ]]; then
        usage
        exit
fi

if [ ! -e "${SH_DIR_DEV}${DOMAIN_NAME}" ]; then
        echo "Domain name ${DOMAIN_NAME} does not exist, aborting."
        exit
fi

echo "Checking out repository..."
svn checkout http://svn.${DOMAIN_NAME} ${SH_DIR_DEV}${DOMAIN_NAME}/dev

echo "Updating ownership and mode..."
chown -R www-data:www-data ${SH_DIR_DEV}${DOMAIN_NAME}/dev

echo "Clearing cache directories..."
rm -fr `find ${SH_DIR_DEV}${DOMAIN_NAME}/dev -type d -name .svn`

```

Thanks in advance,
Ash

---

### Post by furtypajohn on 2011-06-29
> **H3110 said:**
> 
I have a process where by all SVN repositories are held in **/var/svn/[domain]**. I have set-up a post-commit hook to automatically checkout the repository to the development site and delete all .svn directories recursively through-out.


You should check out the export command for svn. It does a clean (read: no .svn folders) checkout of a repository.

```
svn export --help
export: Create an unversioned copy of a tree.
usage: 1. export [-r REV] URL[@PEGREV] [PATH]
       2. export [-r REV] PATH1[@PEGREV] [PATH2]
```As for the actual problem: Is it prompting you to enter your SVN password? If so you could automate the entry of your password using Expect.

See: [http://www.linux.com/archive/feed/56066](http://www.linux.com/archive/feed/56066)

---

### Post by H3110 on 2011-06-29
Thanks for your response, i will look this up!

However, i did a alternative method which, checksout using "file:///var/... /var/www/..."

then i did a "rm -fr `find ...`" to remove all .svn recursively.

Your way is more efficient though and I will implement such practice!

Thanks :)

---

