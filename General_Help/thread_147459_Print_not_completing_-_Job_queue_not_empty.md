---
title: "Print not completing - Job queue not empty"
date: 2006-03-20
forum: General Help
---

### Post by SteveF on 2006-03-20
I've recently installed an HP Photosmart 7850.  Whenever I print to it, the print queue shows the job still printing even though the printing has finished.  The page is printed without problems and is ejected by the printer.  Everthing is fine except the queue.  It shows a job still printing and the only way to print anything else is to cancel the job.

Any ideas?

Thanks,

Steve

---

### Post by gnu2tux on 2006-03-20
I've had that before.

The only way I had to remove the job was to delete it from the queue as root in the terminal window:

```

$sudo bash  (becomes root)
Password: <your pass>
#lpq
(shows printer q)
Job ID   Job
5         My file.ods

so, to remove this job, do as follows

#lprm 5

where 5 is the job id of the print job.

```

hope that helps.

---

### Post by SteveF on 2006-03-20
I've been able to clear it from the printer dialog without having to drop to a console.  But it happens every print and I don't want to have to do that clearing every time.  Or, are you saying that whne you cleared using the console, the issue did not happen again?

Steve

---

### Post by SteveF on 2006-03-20
Fixed the problem.  I decided that may be the install messed up cups somehow so I restarted cups and it cleared up my prblem.  I didn't think of tyring that prior to posting the message.  When in doubt - restart, I guess.

Steve

---

