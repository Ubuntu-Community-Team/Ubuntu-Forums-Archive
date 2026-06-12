---
title: "Setting default read-write permissions on new directories"
date: 2009-11-29
forum: General Help
---

### Post by remino on 2009-11-29
Is it possible to set the default attributes on files and directories created within a specific directory?

I'm trying to look for a way to create a directory in which users part of a group can create new files
and directories and make it writable to the entire group automatically. I still need the usual 0600 attributes for files created outside that specific category and users will create files using SFTP. They are not comfortable with the terminal. For these reasons, using umode is out of the question.

I tried using "chmod g+s", but this only preserves the gid set on new files, not attributes. (I need both, so chmod got me half way there.)

So, any ideas? Thanks in advance!

---

### Post by sisco311 on 2009-11-29
Hi and welcome to the forums!

You have to enable ACL support on the partition where the shared directory is, then set the permissions:

```
sudo setfacl -Rdm g:**group**:rwx /media/share
sudo setfacl -Rm g:**group**:rwx /media/share
```

where group is the name of the group and /media/share is the path to the directory.

[uhelp]community/UbuntuLTSP/ACLSupport[/uhelp]

---

### Post by remino on 2009-11-29
Thanks for the tip! I installed the ACL package yesterday, and enabled it on the mounted filesystem, but didn't know about the default attributes.

The main directory I'm trying to change the permissions for is already owned by the group I want to give the "write" privilege to. Here's what I did, as root:

```

1# apt-get install acl
2# vi /etc/fstab
3# mount -o remount / 
4# cd directory_to_change_permissions
5# chmod -R g+w .
6# find d in `find . -type d`; do chmod  g+s $d; setfacl -dm g::rwx $d; done 

```

[LIST=1]
[*]Install the ACL package.
[*]Edit the "fstab" file to add the "acl" to the "/" filesystem.
[*]Re-mount the "/" filesystem.
[*]Change into the directory I want to change attributes for.
[*]Make all the files and directories writable, recursively.
[*]Find all the sub-directories and set the sticky attribute for the group and set the default for group as writable. 
[/LIST]

This worked! Now, when a user goes into that directory and creates a new file or a new directory, the uid is preserved, the gid is set to the same as the directory, and it is writable by the group. The same will happen when creating a new file or directory within a sub-directory.

I'm using this for a development Web server. All the Web files are in the home directory of a dummy user. All the developers are part of the same group as the dummy user. When one of the developers create a directory or a file in the Web root, other developers can still edit or delete those items.

Thank you for the help!

---

