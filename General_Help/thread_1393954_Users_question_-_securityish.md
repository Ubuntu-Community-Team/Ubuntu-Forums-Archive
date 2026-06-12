---
title: "Users question - securityish"
date: 2010-01-30
forum: General Help
---

### Post by Zorgoth on 2010-01-30
If I were to add someone else as a "Desktop User" in Users and Groups is there anything other than their home directory and /tmp that they could change?

(Xubuntu 9.10)

---

### Post by tom.swartz07 on 2010-01-30
> **Zorgoth said:**
> If I were to add someone else as a "Desktop User" in Users and Groups is there anything other than their home directory and /tmp that they could change?

(Xubuntu 9.10)

By default, Im not sure- I do know that you could go in and change the settings though. Just open "users and groups" from the administration panel and tweak the settings to your hearts content!

---

### Post by Ordes on 2010-01-30
depends...

first of all they are not able to issue sudo commands...

means they cannot go into the terminal and change permission ownerships that are outside of the /home,  or any other folders that u allow them to go.

Lets say your admin, user2 = desktop, 

1) rwxrwx---(770) admin:admin >> user:group are both admin, none for others... so desktop cannot make any changes at all
2) rwxrwx---(770) admin:desktop  >> group desktop can acess, read and write the folder.. therefore also can delete it...
3) rwx------(700) admin:desktop  >> group is desktop but has no permission so cannot do anything

>> when setting "desktop" the user will only have permissions in his /home
, and or in directories that allow others... what kind of permission depends on the settings (write, read, execute)
>> if admin creates folders, partitions, etc, it in his choice to allow dekstop or not... if not allowed desktop has no chance to change this...
>> if admin gives a 7 (write read execute) to any folder, that has group or user desktop, >> dekstop can do anything in this folder that he wants to 

>> read through chown chmod.. try to understand the meaning of ownership and permissions... and u can allow desktop to act the way u like...

---

