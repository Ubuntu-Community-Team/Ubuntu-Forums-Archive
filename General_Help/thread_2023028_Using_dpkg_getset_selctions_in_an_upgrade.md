---
title: "Using dpkg get/set selctions in an upgrade"
date: 2012-07-11
forum: General Help
---

### Post by sd@ksu on 2012-07-11
I have recently installed 12.04 on my system. Earlier I had 11.04. I have both of them installed (using vmware). Now the problem is, I used a few programs in 11.04 and I also want them to be in 12.04. So what I did is as below:
In 11.04:
```
dpkg --get-selections > programlist

```
Then copied it to 12.04 and then I did
```

sudu apt-get update
sudo dpkg --set-selections < programlist
sudo dselect

```
.................................
Now I am in 12.04. The installation took hours...and installed many programs which I was using in 11.04. I can do
```
dpkg --get-selections > programlist-new

```
in 12.04 to get the list and compare with programlist and check for a few of them that thy are installed. But my worry is the following:
1) Will it install some unnecessary programs from 11.04 which is not used in 12.04 anymore and such giving rise to some conflicts later?
2) How can I be sure that all of them got installed? The list before and after installation is a long one..
I thought about trying "diff programlist programlist-new" with appropriate options to compare them but am not sure if that will solve the purpose. Please help. 
My aim is to install the extra programs I have added from repository after 11.04 installation to 12.04. Nothing extra is needed. Also, if I prepare a list of the extra programs (which i need), can i install them all from the file?

---

### Post by drs305 on 2012-07-11
I used this method for years to make sure I had my programs when I did a clean installation of a new release. As you are finding out, the list can be quite long.

The generated list contains the major packages and will bring over the necessary dependencies when you run the import command. The system should prevent dependency problems and will prioritize them if it does find issues.

As for knowing whether the importation was successful, the terminal will provide output for failures (as well as progress during the installation). If you don't notice any failures as the command runs you can probably view the Log Viewer to see what packages might have failed. Using the "grep" command to limit results can pinpoint things pretty quickly. For instance, if you use grep with "status installed" in the Log Viewer's dpkg log you can slim down the results to something manageable.

These days I find that even though I often upgrade there aren't thousands of packages I absolutely must have. I just keep a list in a text file and run a script to install them on the new system.

My text list looks like the output from --get-selections (without the 'install', since I know that's what I'll be doing). I've just manually entered about 40 of them in a list:
> 
htop
geany
audacity
pavumeter

And then I just run this part of my installation script:
```
cat /mnt/data/.masters/preferred.pkgs
read -p "Installing preferred apps. Press s to skip.   " p
for i in $(cat /mnt/data/.masters/preferred.pkgs); do
sudo apt-get install -y $i ; done

```
The 'dpkg' method you described might be overkill, but if you aren't worried about disk space it probably won't hurt either.

---

### Post by Cheesehead on 2012-07-11
> **sd@ksu said:**
> 1) Will it install some unnecessary programs from 11.04 which is not used in 12.04 anymore and such giving rise to some conflicts later?

Yes, you have probably installed some uneccessary packages. Stuff you have forgotten you installed, and will never use again.
No, it's unlikely to cause conflicts. 

Generally, I keep a short list of the applications I actually use (like drs305). The package manager will handle all the thousands of dependencies - that's why we have it.


> **sd@ksu said:**
> 2) How can I be sure that all of them got installed?

If there was no error message, then they all got installed.
If something didn't get installed, so what? Simply add it later.


> **sd@ksu said:**
> 1) My aim is to install the extra programs I have added from repository after 11.04 installation to 12.04. Nothing extra is needed. Also, if I prepare a list of the extra programs (which i need), can i install them all from the file?

Yes, but that's doing it the hard way. Just put them list of packages in a text file, as described by drs305.

---

### Post by sd@ksu on 2012-07-13
Thanks...am not marking it SOLVED yet...because I am still to try thy suggestions...:-)

---

### Post by Vaphell on 2012-07-13
```
for i in $(cat /mnt/data/.masters/preferred.pkgs)
do
  sudo apt-get install -y $i
done
```

not that it makes any difference here, but in general one should use *while* loop to read data from files without resorting to *cat*. It works on per-line basis and almost entirely ignores problems with whitespaces, which are rampant with *for* loops.

```
while read prog
do
  sudo apt-get install -y $prog;
done < packages.txt
```

---

### Post by drs305 on 2012-07-13
> **Vaphell said:**
> 
not that it makes any difference here, but in general one should use ...

Thanks. I haven't had lessons in scripting in almost 40 years and don't remember a thing.  ;-)

---

