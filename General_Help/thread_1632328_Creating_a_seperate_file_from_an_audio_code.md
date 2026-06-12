---
title: "Creating a seperate file from an audio code"
date: 2010-11-27
forum: General Help
---

### Post by rmcellig on 2010-11-27
As you can see from the attached file, I have a cron running every hour, but what is happening is that the script is writing to the same file instead of creating a new file every time it records the audio. What do I need to do so that every hour, a new file is created instead of writing to the same file every hour?

---

### Post by iNsOmNiOuS on 2010-11-27
Try using a random name for the file, possibly by using Bash's $RANDOM output. I don't know how to integrate that into a Cron job though

---

### Post by mc4man on 2010-11-27
Add something to saved file name, perhaps date and time
"$(date +%F-%T)"

testmodulehour-"$(date +%F-%T)".wav

---

