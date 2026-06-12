---
title: "Shell script to shutdown virtual machines. copy, and than start VM"
date: 2011-03-16
forum: General Help
---

### Post by garethsimpsonuk on 2011-03-16
Hi all,

I need to make my 1st ever script to backup VMware workstation VMs to a folder which is then backed up offsite.

Here is what I have so far (will be croned):

```

sudo vmrun -T ws  stop "/home/gareth/vmware/NagiosWeb/NagiosWeb.vmx" soft

sudo vmrun -T ws  stop "/home/gareth/vmware/UbuntuBackup/UbuntuBackup.vmx" soft

**copy or rsync to /home/gareth/vmware-backup/ dir**

sudo vmrun -T ws  start"/home/gareth/vmware/NagiosWeb/NagiosWeb.vmx"

sudo vmrun -T ws  start "/home/gareth/vmware/UbuntuBackup/UbuntuBackup.vmx"


```

The commands on their own work but I'm unclear on the below:

[LIST=1]
[*]Just to confirm, I need to place the above in a file with #!/bin/bash at the top and make it executable
[*]How do I know when the VMs have safely shut down so I can start the copy? I guess I can either a. wait a specified amount of time b. run some sort of if statement to confirm they are off
[*]How do I use Rsync or cp to copy to the backup folder?
[*]How will I know the copy is complete so that I can start the VMs again?
[/LIST]

Any help would be greatly appreciated. Thanks

---

### Post by NIN101 on 2011-03-16
> 
Just to confirm, I need to place the above in a file with #!/bin/bash at the top and make it executable

You can start the shellscript by using **bash [path to the script]** or sh (depends on the shell the script has been written for) etc. 

But if you want to execute the script "like normal programs", then you are right.

> How do I know when the VMs have safely shut down so I can start the copy? I guess I can either a. wait a specified amount of time b. run some sort of if statement to confirm they are off

If vmrun is a good program, it should exit when the job is done (except it is using daemons (or even then) ). 

Yes, you can wait some time with "sleep". For example, **sleep 5** will wait 5 seconds until the next commands will be executed.

"watch" is a better solution.
```

watch -e lsof [path to .vmx file] > /dev/null
[other commands]

```

This command will check every 2 seconds if the .vmx file is open. Once it is closed, the shellscript will continue(When the -e option for "watch" is given, watch will execute the command(lsof in this case) until it returns an error(which means that the file isn't open anymore in this case). This is only needed if vmrum doesn't exit when the virtual machine is stopped. 



> How do I use Rsync or cp to copy to the backup folder?

```
cp /home/gareth/vmware/NagiosWeb/NagiosWeb.vmx  /home/gareth/vmware-backup/
``` 

> How will I know the copy is complete so that I can start the VMs again?
You don't have to care. 

You should read a tutorial about shellscripting :-).

---

