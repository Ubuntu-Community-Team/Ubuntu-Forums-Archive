---
title: "Killing all the process on restart/halt/shutdown instead waiting for scripts"
date: 2010-05-09
forum: General Help
---

### Post by nullzone on 2010-05-09
Hi there,

   I haveing a big problem atm (just after to upgrade to 10.04).

   I have a simply and easy script that sent a halt command to every KVM virtual machine actually running into the server.  this script is/and was) palced as a init-rc script in rc0/rc1 and rc6 lvls.

   Just after to upgrade, I have noticed that this script is executed but the system ignore the time that it require to finish (giving time to correctly stop a single virtual machine). Aftert 5 second it start sending SIG-TERM and SIGN-KILL to any currect process and then reboot/halt.

   I have just done a new script using upstart and I got just the same result.

   What is happending? why is the waiting the init secuence for a valid/or_not termination of any init script.

   I am so sorry for this crap english ... I have never study this language so I try to do my best anytime I speak it (or try ti..).

Thanks by any advance.

:confused:

---

### Post by dcstar on 2010-05-10
> **nullzone said:**
> Hi there,

   I haveing a big problem atm (just after to upgrade to 10.04).

   I have a simply and easy script that sent a halt command to every KVM virtual machine actually running into the server.  this script is/and was) palced as a init-rc script in rc0/rc1 and rc6 lvls.

   Just after to upgrade, I have noticed that this script is executed but the system ignore the time that it require to finish (giving time to correctly stop a single virtual machine). Aftert 5 second it start sending SIG-TERM and SIGN-KILL to any currect process and then reboot/halt.

   I have just done a new script using upstart and I got just the same result.

   What is happending? why is the waiting the init secuence for a valid/or_not termination of any init script.

   I am so sorry for this crap english ... I have never study this language so I try to do my best anytime I speak it (or try ti..).

Thanks by any advance.

:confused:

10.04 is designed to shut down quickly and it will try and kill any processes during the shutdown process.

Unless your script is run before **S20sendsigs** in rc0.d & rc6.d then those processes will get killed off as a group by that script.

---

### Post by nullzone on 2010-05-10
OK, it is now SOLVED.

There are several issues to solve in these situations...

Actually, I had several problems. 
1) sysv-init scripts are now using a "set -e" / "sh -e". So you need to take care with your all scripts evading to executing commands and getting their return values as a valid way. As soon as any command fails, the script will stop. Ex: "ps --pid XXX" when XXX process is not available anymore. ps will return a "error" value that you will nto be able to catch using $? as a usual script. 
2) Just in my case, I was trying to stop virtual machines from a sysv-init script (placed before the S20sendsigs). Problem was that upstart is calling rc (sysv-init scripts) at the same time than any other when you are chancing to a "byebye" RUNLEVEL. Having in mind that Ubuntu has yet the _sendsigs_ _killall_ into the sysv-init scripting.. it is a big problem. In my case, libvirt-bin was being stoped by upstart before I was arriving to the the script in the rc-sysv that was needing that libvirt-bin available yet. So, when I was trying to use the libvirt interface/sock to shutdown the virtual machines it wasnt already available. To solve this I have removed the stop in the upstart and I am stoping it from my own script in the sysv-rc side.
3) I was trying to move my sysv-rv script to upstart. So, I could change the libvirt-bin stop call to be executed as soon as the stop event from by script was being called. Well, It doesnt work as well. Problem here is really really dangerous btw... and it is really important that ppl have in mind this problem in the actual ubuntu release.
Since rc-init is called from upstart as soon as you change the RUNLEVEL (sysv compatibility), and having in mind that your are calling the sendsigns/killall from a script in the sysv init,  you dont control really any stop in the upstart.
I mean that, as soon as you change to the lvel 0 or 1 or 6 (for example), you will have 2 lines of execution:
line 1: any process configured to be stoped from upstart when you go into those levels (that is, any procress really at lvl 0 and 6)
line 2: the sysv-rc scripting that has been invoked in a paralel way by upstart but moves really independent.
The problem is that if you have your _stop_ scripts in upstart and you continue using the sysv to send the TERM/KILL (as Ubuntu does), the line 2 os execution (SYSV) is going to travel pretty quick. In conclusion, you are going to arrive into the S20sendsigs really quick. Any 'stop' call that need some time to be executed (just think that you are stoping a database, for example, something that need some time to be correctly executed, or some virtual machines ;-) ) are going to be killed by S20sendsigs since you are going to call that script regardless of whether you need that those stop finish before to send all those TERM signals.


So, while Ubuntu continues holding the TERM/KILL scripting into the SYSV system, you should stay using the SYSV style for stoping any procress (at least if you need to do a controlled stop to dont lose any information ... to KILL a process is not usually a good way to stop some type process as databases, virtualmachines or simply any procress with cache/unsaved information/openfiles).

GL

Again, I am sorry about my crapy english. I hope that it will be understable.

---

### Post by rlaager on 2010-05-10
nullzone: If you've solved this, do you have some working scripts you could share? I'm working on the same problem right now.

---

### Post by nullzone on 2010-05-11
I am just from my cellular atm. I will do it as soon as I arrive at home. 

Cheers

---

### Post by dcstar on 2010-05-11
> **nullzone said:**
> OK, it is now SOLVED.

There are several issues to solve in these situations...
........
So, while Ubuntu continues holding the TERM/KILL scripting into the SYSV system, you should stay using the SYSV style for stoping any procress (at least if you need to do a controlled stop to dont lose any information ... to KILL a process is not usually a good way to stop some type process as databases, virtualmachines or simply any procress with cache/unsaved information/openfiles).

GL

Again, I am sorry about my crapy english. I hope that it will be understable.

It will be good to see your solutions to this, there is an long-standing bug where Ubuntu will not play the logout sound at shutdown/reboot because the sound server is killed off. If you can solve your problem it may also apply to this problem.

---

### Post by nullzone on 2010-05-11
> **rlaager said:**
> nullzone: If you've solved this, do you have some working scripts you could share? I'm working on the same problem right now.

Hello again rlaager,

   I was using 2 ways to stop the virtual machines. 

   1st) to do a ssh with a halt command (you need to register a key into the /root/.ssh/authorized_keys etc etc
   2nd) to support ACPI on any of your virtual machines so you will be able to send shutdown events as a "power buttom".

   I am using the 2nd way atm, so, I need to evade that upstart stop the libvirt-bin process before I am using its interface to send shutdowns to the virtual machines (using virsh in my case). If you want to use this way, just remember to have availabkle the ACPI support in your virtual machines (in case they are linux, just install the acpid package). So, to start just edit the file "less /etc/init/libvirt-bin.conf" and comment out the line 5: "stop on runlevel [!2345]". You will evade a premature stop of the libvirt-bin. We will stop it manuallity in our sysv script.

   Now you need to place your sysv script in the init.d and just make a symbolic link with a S10 previous in the name (anything previous to S20). The script is attached.

   If it not the best script at all but it works with a set -e.

Good luck and let me know if I can help you with anything more.

---

### Post by nullzone on 2010-05-11
> **dcstar said:**
> It will be good to see your solutions to this, there is an long-standing bug where Ubuntu will not play the logout sound at shutdown/reboot because the sound server is killed off. If you can solve your problem it may also apply to this problem.

I dont see a valid and elegant way to solve that bug more than to move back the init script of the sound server to the sysv tree until everything is migrated to upstart (by evertything I mean the sendsigs / killall and unmountall :-( ).

With the actual schema, you cant do any "stoping/stoped" reference to the rc upstart process/event (the bridge / compat solutiont o have the sysv working). Since rc (sysv) has inside the sendsigs for everything currently running in the system, any upstart running (trying to stop anything) or just any process at all (except init/kill etc.. that are manually evaded in the scripting) will be terminated as soon as sendsigs is called in the sysv tree. I think that it is a really big problem with the actual scheme where sendsigs are completly uncontrolled and executed ignoring any actual state of those stop process that are running in the upstart.

I dont see a easy way to control from the sysv tree what is happening in the upstart and vice versa :( so, sysv tree shouldnt have any massive term/killall or unmount progress as it has atm (if it is really moving to upstart at some point). From my point of view, the first that should be moved to upstart are the sendsigs/killall/umount and after that the rest ... it is like building a house starting with the roof.

 Anyway, assuming that the shutdown sound is launched from the sysv, and the server from the upstart, it should be possible to do a botch/workarround as I did with libvirt-lib just commenting out the stop in the sound server upstart configfile and do a manual stop from the sysv sound event file just after you have sent the shutdown sound .. but it is really no elegant.

Why isnt that sound event added as a pre-stop into the upstart script or in a new script with a "start on (runlevel [06]
          and (stopping SOUND_SERVER_UPSTART_PROCESS_NAME)" ?

I havent check anything about that tbh, so I dont have a clue about how it is exactly configured and what is really the problem there (what scripts are on sysv and what un upstart etc), also I assume that it is on the desktop version. May you link me the bug tracker url please? I will try to look on that tomorrow if u need it.

---

### Post by dcstar on 2010-05-14
I see on my system that "K" scripts in the rc0.d & rc6.d folders are actually run when shutting down/rebooting to correctly end individual processes, so it should be possible to add in a new "K" script to shut down the database files.

I don't know if the system actually waits for these to complete or it just kicks them off and then kills things whether they have finished or not.

---

### Post by nullzone on 2010-05-15
> **dcstar said:**
> I see on my system that "K" scripts in the rc0.d & rc6.d folders are actually run when shutting down/rebooting to correctly end individual processes, so it should be possible to add in a new "K" script to shut down the database files.

I don't know if the system actually waits for these to complete or it just kicks them off and then kills things whether they have finished or not.

Yes, that works perfectly (placing then in a K below the 20 lvl).

Problems come on everything already migrated to upstart.

---

