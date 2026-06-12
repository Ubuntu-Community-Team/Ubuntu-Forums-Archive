---
title: "unrar-ed files not taking on ACL permissions?!"
date: 2009-11-26
forum: General Help
---

### Post by imxuk on 2009-11-26
Ok... so i have ACL's set on the required directory, however unrar seems to change back the permissions to default?!

# file: ../xxxxx
# owner: xxxxxx
# group: data
user::rwx
user:administrator:rwx
group::rwx
group:data:rwx
mask::rwx
other::---
default:user::rwx
default:user:administrator:rwx
default:group::rwx
default:group:data:rwx
default:mask::rwx
default:other::---

The files created in that directory, the text file which has not been unrar-ed is fine...


drwxrws---+ 2 xxxxxx data   89 2009-11-26 13:02 .
drwxrws---+ 3 xxxxxx data   28 2009-11-26 13:02 ..
-rw-------+ 1 xxxxxx data 256M 2009-11-22 04:02 xxxxxx.avi
-rw-rw----+ 1 xxxxxx data 1.3K 2009-11-26 13:00 xxxxxx.txt

Any ideas?!  The txt file was NOT in the rar, so has the correct permissions....

---

