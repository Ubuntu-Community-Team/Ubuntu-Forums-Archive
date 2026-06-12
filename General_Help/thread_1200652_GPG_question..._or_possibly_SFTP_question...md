---
title: "GPG question... or possibly SFTP question.."
date: 2009-06-30
forum: General Help
---

### Post by bmturney on 2009-06-30
I have a friend that sends me a file via SFTP... it is encrypted with GPG... When he sends it to me I have a bash script that I run that decrypts the file and moves it to another location to be picked up by another process later. When I run the bash script myself with the command "sudo bash ~/scripts/script.sh" it runs beautifully... however if I try to add an entry to /etc/crontab to run this script automatically as root... it can't find the gpg key it needs to decrypt the file.

If I try to set the script up in the user crontab its doesn't have permissions to the file that is uploaded because that file is owned and has the group of the user that uploaded the file... and there are no world permissions set on the file when it is uploaded.. 

so should I copy my secure key so that root can use it to decrypt the file in the cron job... and if so where do I need to copy it?

Or is there a way to set the permissions on files that are uploaded via SFTP so that my user would have access to them automatically?

---

