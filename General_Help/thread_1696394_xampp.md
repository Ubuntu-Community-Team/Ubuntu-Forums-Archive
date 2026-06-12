---
title: "xampp"
date: 2011-02-27
forum: General Help
---

### Post by AlfredVargas on 2011-02-27
Hi there!
I got something to ask and I'm new here in forum. hope someone can help me despite being newbie. I have my final project and that is. 3 laptops connected to each other using switch and each of it is running ubuntu. One of the laptops is used as a web server. I installed already the xampp but my problem is I don't know how to save file in htdocs. In addition, I have no idea how my website in webserver can be viewed by 2 other laptops. It's just an intranet no need to be viewed through internet. Thank you in advance. Really frustrated to finish my project.:razz:

---

### Post by MrRichard on 2011-02-27
Hi, I might be able to help you with your issue about not being able to edit files under htdocs. If you have xampp installed under /opt/lampp try taking ownership of the files by running this command:
```
sudo chown -R usernamegoeshere /opt/lampp
```

---

