---
title: "making a simple update cronjob"
date: 2010-03-29
forum: General Help
---

### Post by PatrickD-52761 on 2010-03-29
Hi everyone,

I'm trying to make a simple auto-update cronjob for Kubuntu 9.10.  I tried it using sudo crontab -e and putting the following in:

0 0 * * apt-get update && apt-get dist-upgrade -y

and it seemed to work (as my system monitor showed a bunch of new processes running for a second).

Then, I tried running a script that had the following code in it:

apt-get update
apt-get dist-upgrade -y >>apt-get-results.log

What I'm trying to accomplish is having it show me whether the upgrade was successful or not.  However this didn't produce any output in the apt-get-results.log file.

I know that apt-get returns 0 if it's successful and 100 if it fails.  And I know that my script is wrong.  What I would like to do is something along these lines inside of the script:

If result==0 then
  echo "Update was successful" ($date) >> apt-get-results.log
else
  echo "Update had errors" ($date) >> apt-get-results.log
fi

So, if anyone could point me in the right direction for the script, that would be greatly appreciated.

Two things to note.  The script that I'm running in the cronjob is located at /bin/apt-get-script  and the results are in my home directory.  So, I'm not sure if that will have an effect on this or not.

In otherwords my crontab will look like this:
0 0 * * /bin/apt-get-script

And my apt-get results will be in /home/username/apt-get-results.log

Thanks, and have a great day:)
Patrick.

I chose "all-variants" because hopefully this will work in all distros of *ubuntu, but I'm running Kubuntu specifically.

---

