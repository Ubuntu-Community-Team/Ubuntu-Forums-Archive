---
title: "How to revert to recommened updates?"
date: 2010-02-15
forum: General Help
---

### Post by blwegrzyn on 2010-02-15
I am running ubuntu 9.10.
Is it possible to remove the pre-released updates and revert to recommended updates?
thx

---

### Post by chaanakya_chiraag on 2010-02-15
I'm not sure, but I know you can deselect the pre-release sources, which ensures you don't get any more pre-released updates.

---

### Post by blwegrzyn on 2010-02-15
i know that, but i want to revert back and the problem is i am not sure which packages are form proposed tree so i could replaced them?

---

### Post by chaanakya_chiraag on 2010-02-15
Try opening /var/log/apt or something like that to see which packages were updated.  Then, go into Synaptic and roll back to the latest stable version.  If you're not sure what the latest version is, just roll it back to the oldest version possible, apply, and check for updates and apply them.

---

### Post by blwegrzyn on 2010-02-15
i wish there would some automatic way to do so?

---

### Post by mcduck on 2010-02-15
> **blwegrzyn said:**
> i know that, but i want to revert back and the problem is i am not sure which packages are form proposed tree so i could replaced them?

You only need to do that if you are having serious problems with one of the updated packages.

Otherwise, simply disabling the proposed-repository again will do the trick in a week or two, as the packages you have updated through the proposed-repository are moved to normal repositories and will be installed as normal updates (if there's any difference betwen the version you got through proposed and the final version).

---

### Post by slakkie on 2010-02-15
apt-cache policy $package

eg:

```

apt-cache policy hello
hello:
  Installed: 2.4-3
  Candidate: 2.4-3
  Version table:
     2.5-1 0
        500 ftp://ftp.nl.debian.org unstable/main Packages
 *** 2.4-3 0
        990 ftp://ftp.nl.debian.org testing/main Packages
        100 /var/lib/dpkg/status
     2.4-3 0
       -200 http://archive.ubuntu.com lucid/main Packages
     2.2-3 0
       -200 http://archive.ubuntu.com jaunty/main Packages
     2.2-2 0
        500 ftp://ftp.nl.debian.org lenny/main Packages

```

Now let's assume I want to install the version from lenny:

sudo aptitude install hello/lenny

or based on version:

sudo aptitude install hello=2.2-2


You might also want to read this, [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/). Think it will provide some insight in how apt works and what you can do.


To match which package comes from which repo, you can use the shell functions below. Put them in your .bashrc, source it (source .bashrc or . .bashrc) and then run repo2pkg <name of repo> eg, repo2pkg proposed


```

repo2pkg () {
        local frepos=$@
        local repos
        for pkg in $(dpkg -l | grep '^ii'| awk '{print $2}' )
        do
                repos=$(pkg2repo $pkg)
                if [ -z "$frepos" ]
                then
                        [ -n "$repos" ] && echo -e "$repos"
                        continue
                fi
                for i in $frepos
                do
                        echo -e "$repos" | grep -w "$i"
                        [ $? -eq 0 ] && break
                done
        done
}

pkg2repo () {
        [ -z "$1" ] && return
        local pkg="$1"
        local policy
        local cur
        local can
        local upgrade
        for pkg in $@
        do
                policy=$(apt-cache policy $pkg)
                cur=$(echo -e "$policy" |  grep Installed | awk '{print $NF}')
                can=$(echo -e "$policy" |  grep Candidate | awk '{print $NF}')
                upgrade="$cur"
                [ "$can" == "(none)" ] && can=$cur
                [ "$can" != "$cur" ] && upgrade="U: $cur > $can"
                repos=$(echo -e "$policy" | grep "$can" -A1 | egrep "(http|ftp|smb|cdrom|nfs|file)://" | tail -1 | awk '{print $2" "$3}')
                local msg
                msg="%-35s %-45s %s\n"
                [ -n "$repos" ] && printf "$msg" "$pkg" "$upgrade" "$repos"
        done
}

```

---

### Post by blwegrzyn on 2010-02-15
> **mcduck said:**
> You only need to do that if you are having serious problems with one of the updated packages.

Otherwise, simply disabling the proposed-repository again will do the trick in a week or two, as the packages you have updated through the proposed-repository are moved to normal repositories and will be installed as normal updates (if there's any difference betwen the version you got through proposed and the final version).

so after two weeks any packages that was installed from proposed repository will be downgraded to whatever is in recommended repository?

---

### Post by blwegrzyn on 2010-02-15
thx mcduck the script helped me to find the packages,
now i can use the force version to downgrade,
thx a lot, i hope this will fix my ubuntu and it will fix my problem with the services not starting,

---

### Post by mcduck on 2010-02-15
yep, the proposed repository is used for testing update packages before they are moved to normal repositories.

It usually takes from couple of days to couple of weeks for the packages to move from proposed to normal updates. So if you disable the proposed repository now after a while all the packages you have downloaded from there will have been made available through normal repositories, and everything will be as if you had never even enabled the proposed repo.

If some of the packages gets some fixes before being moved to normal repositories you'll just get the fixed version as a normal update exactly like everybody else does.

So I really wouldn't bother removing the packages you got from the proposed, after a while you'll just get the same packages again from normal repositories. :)

---

