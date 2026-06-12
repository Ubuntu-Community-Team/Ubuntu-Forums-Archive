---
title: "Why I can't execute a symlink in /etc/init.d?"
date: 2011-08-22
forum: General Help
---

### Post by ZequeZ on 2011-08-22
So, I made a bash script that I need to be executed on booting, I created it in /etc/sbin/mount_folder.sh

```

sudo chmod +x mount_folder.sh
sudo ln -s mount_folder.sh /etc/init.d/mount_folder.sh

```

Then I try to:

```

sudo update-rc.d mount_folder.sh defaults
update-rc.d: /etc/init.d/mount_folder.sh: file does not exist

```

So I tried to execute it manually

```

sudo ./etc/init.d/mount_folder.sh
sudo ./etc/init.d/mount_folder.sh: command not found

```

Also:

```

ls -l mount_folder.sh
-rwxr-xr-x 1 root root 88 2011-08-22 04:05 mount_folder.sh
ls -l /etc/init.d/mount_folder.sh
lrwxrwxrwx 1 root root 15 2011-08-22 04:14 /etc/init.d/mount_folder.sh -> mount_folder.sh

```

Also, if I create the symbolic link in the same folder I can execute it normally :|

So, what's wrong?

---

### Post by fdrake on 2011-08-22
```

sudo update-rc.d mount_folder.sh defaults
update-rc.d: /etc/init.d/mount_folder.sh: file does not exist

```

update-rc.d makes link whose file target is in /etc/ini.d
that's why it cannot create the link because you are creating a symbolic link from another symbolic link.

```

sudo ./etc/init.d/mount_folder.sh
sudo ./etc/init.d/mount_folder.sh: command not found

```

it should be :
sudo /etc/init.d/mount_folder.sh (with no "." )

try :
```
sudo mv mount_folder.sh /etc/init.d/mount_folder.sh
ln -s /etc/init.d/mount_folder.sh ~/Desktop/mount_folder.sh # in case you want to edit it 
sudo update-rc.d mount_folder.sh defaults
```

---

### Post by ZequeZ on 2011-08-22
> **fdrake said:**
> 
update-rc.d makes link whose file target is in /etc/ini.d
that's why it cannot create the link because you are creating a symbolic link from another symbolic link.


The update-rc.d takes a name as a parameter, not the whole path. At least that's that `man update-rc.d` says.
Unless you mean that update-rc.d can't accept symlinks, but that wouldn't explain why I can't execute it manually with sudo /etc/init.d/mount_folder.sh

> **fdrake said:**
> 
it should be :
sudo /etc/init.d/mount_folder.sh (with no "." )


I still can't execute the script, not even with the correct path, also the tab key does not autocomplete me the /etc/init.d/mount_folder.sh, so it is not being taken as executable.

> **fdrake said:**
> 
try :
```
sudo mv mount_folder.sh /etc/init.d/mount_folder.sh
ln -s /etc/init.d/mount_folder.sh ~/Desktop/mount_folder.sh # in case you want to edit it 
sudo update-rc.d mount_folder.sh defaults
```


Without the symlink it works, moving the original file to /etc/init.d/mount_folder.sh do allows me to execute it. But I was hoping to have the original files placed in /usr/local/sbin =/

Also, with a hard link it works correctly

---

### Post by fdrake on 2011-08-22
from manual
> update-rc.d updates the System V style init script links /etc/rcrunlevel.d/NNname  whose  target  is  the  script
       /etc/init.d/name.

> 
I still can't execute the script, not even with the correct path, also the tab key does not autocomplete me the /etc/init.d/mount_folder.sh, so it is not being taken as executable.

what is the error message ? no permission or no file found?

---

### Post by ZequeZ on 2011-08-22
> **fdrake said:**
> from manual



what is the error message ? no permission or no file found?

No file found, but it is there.

Anyhow, don't worry anymore, I ended adding the script path to rc.local ^^

Thanks ^^

---

### Post by fdrake on 2011-08-22
it looks like that update-rc.d  in ubuntu is a little different than the one in other distros like gentoo, where you can  simply add/remove the script. basically in ubuntu it check if it is a link to a specific file in /etc/init.d/ and then if true it executes it.


```

 less /usr/sbin/update-rc.d
---------------------------------------------------
sub checklinks {
    my ($i, $found, $fn, $islnk);

    print " Removing any system startup links for $initd/$bn ...\n"
        if (defined $_[0] && $_[0] eq 'remove');

    $found = 0;

    foreach $i (0..9, 'S') {
        unless (chdir ("$etcd$i.d")) {
            next if ($i =~ m/^[789S]$/);
            die("update-rc.d: chdir $etcd$i.d: $!\n");
        }
        opendir(DIR, ".");
        my $saveBN=$bn;
        $saveBN =~ s/\+/\\+/g;
        foreach $_ (readdir(DIR)) {
            next unless (/^[SK]\d\d$saveBN$/);
            $fn = "$etcd$i.d/$_";
            $found = 1;
            $islnk = &is_link ($_[0], $fn, $bn);
            next unless (defined $_[0] and $_[0] eq 'remove');
            if (! $islnk) {
                print "   $fn is not a link to ../init.d/$bn; not removing\n"; 
                next;
            }
            print "   $etcd$i.d/$_\n";
            next if ($notreally);
            unlink ("$etcd$i.d/$_") ||
                die("update-rc.d: unlink: $!\n");

```

---

