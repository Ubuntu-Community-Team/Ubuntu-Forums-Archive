---
title: "simple yet hard..."
date: 2012-02-25
forum: General Help
---

### Post by saders on 2012-02-25
hello all

this script helps me to take auto screen-shots for specific time interval but got bumped on a step i have created a user(not admin) and added it on startup application too the problem now is that all the files are being saved in home folder and the user is able to see and delete the files so is there any way that i can make the destination folder in admin folder or my desired location and make sure they can see it but not delete it..???


bootmgr_dir='DFsystemtwo';
seconds='30';
if [ ! -d "$bootmgr_dir" ]; then
mkdir $bootmgr_dir;
fi
while true; do
sleep 10;
(scrot -q 50 $bootmgr_dir/t5p5-$(date +%k.%M.%S_%d.%m.%Y|sed -e 's/^ *//').jpg) &
done

---

### Post by ajgreeny on 2012-02-25
Try adding the script contents to **/etc/rc.local** just above the "exit 0" line.  It should then be run at boot time and the scrot image files will all be put into a folder in the root filesystem called /bootmgr_dir, and I think will be owned by root, so only admin users will be able to delete them, but should be able to see them.

I imagine there are many other ways to do this, but this is the only way I am aware of at present.  Give it a go; if it's not successful you can just edit the script lines out of /etc/rc.local.

---

### Post by saders on 2012-02-26
it did not work :( also my friend gave me another script please look into this as we got 300 systems here and we make 1 user acct and 1 admin acct so we name our PC like for guest user01 another acct admin01 for admin use , user02 admin02 like this it goes on now i want all user02 screen-shot files to be automatically moved to given address below but even with the script it is not working so kindly help me to solve this problem asap...

DF=down floor
TF=top floor
numbering=DF/TFsystemone


while true; do
sleep 0;
mv /home/user3/Dfsystemthree/*.jpg /home/pc03/systemsys/DFsystemthree/ &
done

---

