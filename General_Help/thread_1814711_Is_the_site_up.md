---
title: "Is the site up?"
date: 2011-07-30
forum: General Help
---

### Post by Kissell on 2011-07-30
anyone know a way from the command line way from ubuntu to test if a website is up?  

there are websites where you can manually check, but i want to check several sites, not just ones i'm hosting on my ubuntu systems...  and send myself an e-mail if any of them are down.

---

### Post by fdrake on 2011-07-30
is your site live (online, registered or just on your server)?

---

### Post by Kissell on 2011-07-30
Originally I just wanted to send mail if apache was down...  but now I decided I would rather test if a URL is reachable, so that I can be notified that sites not hosted locally are unreachable.

I found this code, at [askubuntu]("http://askubuntu.com/questions/27954/how-can-i-check-internet-connectivity-in-a-console") testing it now, looks like it should work:
> 
wget --spider [http://example.com](http://example.com)
if [ "$?" != 0 ]; then
  echo "Website failed!" | mail -s "Website down" [email]your_email@provider.tld[/email]
fi


---

### Post by papibe on 2011-07-30
There's several options. Do you want to do it interactively or with some automation on a script?

Some ideas:
[LIST=1]
[*]CLI browser called w3m.
[*]CLI browser called lynx.
[*]Use wget to download the home page.
[*]Double check by using the site [http://www.downforeveryoneorjustme.com/]("http://www.downforeveryoneorjustme.com/")
[/LIST]

Regards.

---

### Post by Kissell on 2011-07-30
I can do it manually...  that isn't useful.  The purpose is for the server to check periodically for me and e-mail me only if it is down...  that way I can be out on the beach or watching a movie and days or weeks won't go by before i realize my site has been down all that time.

---

### Post by Kissell on 2011-07-30
Obviously if the server itself is down, it won't be running the script, so using another server as a client to check the way a client would, is much less prone to failure.

---

### Post by Kissell on 2011-07-30
This code should work, yanked it from another site.
Except, I don't understand the code.  He sets the variable "FLAG" to 1 if successful, yet then it appears he tests for if FLAG is equal to 1 and if so send a message that the site is down.

> 
#!/bin/bash

# Sending the output of the wget in a variable and not what wget fetches
RESULT=`wget --spider [http://blog.ashfame.com](http://blog.ashfame.com) 2>&1`
FLAG=0

# Traverse the string considering it as an array of words
for x in $RESULT; do
    if [ "$x" = '200' ]; then
        FLAG=1 # This means all good
    fi
done

if [ $FLAG -eq '0' ]; then
    # A good point is to check if the internet is working or not
        # Check if we have internet connectivity by some other site
        RESULT=`wget --spider [http://www.facebook.com](http://www.facebook.com) 2>&1`
        for x in $RESULT; do
            if [ "$x" = '200' ]; then
                FLAG=1 # This means we do have internet connectivity and the blog is actually down
            fi
        done

    if [ $FLAG -eq '1' ]; then
        DISPLAY=:0 notify-send -t 2000 -i /home/ashfame/Dropbox/Ubuntu/icons/network-idle.png "Downtime Alert!" "http://blog.ashfame.com/ is down."         
    fi  
fi

exit


---

### Post by Kissell on 2011-07-30
oh, the minus is the negation symbol in bash?  ok

---

### Post by Wim Sturkenboom on 2011-07-30
> **Kissell said:**
> Obviously if the server itself is down, it won't be running the script, so using another server as a client to check the way a client would, is much less prone to failure.

Possibly a better option is to let them both send you an email.

---

### Post by Kissell on 2011-07-30
> **Wim Sturkenboom said:**
> Possibly a better option is to let them both send you an email.

I only want to get one e-mail and I don't care the reason it is down, down is down from the user perspective.  It could be my DNS host, whatever, doesn't matter why as long as I am notified.

It would be really nice if one of those sites like [isup.me]("http://isup.me") would let you register to create an account and provide this notification service.

---

