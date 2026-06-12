---
title: "I need PHP"
date: 2011-03-30
forum: General Help
---

### Post by sofasurfer on 2011-03-30
I need  PHP (version 4.4.x or higher) but I do not see it in synaptic. Do we have it?

---

### Post by CharlesA on 2011-03-30
Just install php5:

```
sudo apt-get install php5
```

---

### Post by fragos on 2011-03-31
Just to make sure you know, PHP only runs in a web server. To execute PHP on your local desktop you'll need to install the apache2 web server and configure it to allow PHP.

---

### Post by CharlesA on 2011-03-31
> **fragos said:**
> Just to make sure you know, PHP only runs in a web server. To execute PHP on your local desktop you'll need to install the apache2 web server and configure it to allow PHP.

Valid point. You can install LAMP, but running this and selecting LAMP Server:

```
sudo tasksel
```

If you don't need MySQL, then you can just install apache and php like so:

```
sudo apt-get install apache2 php5
```

---

### Post by Dave_L on 2011-03-31
Although php is primarily used for web programming, it can also be used as a command line scripting client, with the package php5-cli.

---

### Post by WorMzy on 2011-03-31
I'm just being pedantic here, but you don't actually need a webserver to run php code. PHP is a scripting language, and it comes with it's own interpreter (if you install the php5-cli package).

```
php5 path/to/script.php
```

Will run a php script without the need to install a webserver. Obviously, if the script just generates (X)HTML, then it'll just print it to stdout.

EDIT: I write slow. :)

---

### Post by fragos on 2011-03-31
I wasn't aware of php5-cli -- glad you guys corrected my error.

---

