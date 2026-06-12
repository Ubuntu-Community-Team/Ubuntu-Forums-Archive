---
title: "Broken packages"
date: 2006-04-21
forum: General Help
---

### Post by kitts on 2006-04-21
i cannot any application either with 'dpkg -i ' or apt-get install' . All commands given me the same result..Dependency errors  packages broken..
i cannot open any video file totem player because there are no codecs ..even avi installed.
       No new program can be installed. Help me:confused:

---

### Post by kingmonkey on 2006-04-21
try "sudo apt-get check" and "sudo apt-get install -f"

---

### Post by kitts on 2006-04-22
[QUOTE=kingmonkey]try "sudo apt-get check" and "sudo apt-get install -f"[/QUOTE]
it says there are no updates. o updates, o broken etc....

                      **  Is there a way out of this Dependency loop**?:confused: 
Is there any third party program to install these programs without giving dependency errors. 
                        i just can't install anything other than what is provided on the cd.iso](*,) 
                Anyway what are these dependencies?

---

### Post by kingmonkey on 2006-04-23
What are the dependency errors?

Trying as "sudo apt-get dist-upgrade" sometimes resloves dependecy problems.

---

