---
title: "magic_quotes settings  php.ini"
date: 2010-05-07
forum: General Help
---

### Post by Joe325 on 2010-05-07
Hi Experts,

I have an Ubuntu 9.10 Server Edition that I enjoy messing up and fixing. I have 2 pieces of Web Software in the /var/www/ that has issues with the magic_quotes settings in 
/php5/apache/php.ini. 
The problem is that 1 once the settings off - and the other wants them on. 1 of them is atmail web client and the page will not load if the settings are off and the other just errors on the index page saying I need them on.
Is there are way I can have the best of both Worlds..... ;)

Thanks

---

### Post by Joe325 on 2010-05-09
Hmm - I guess this cant be done:(

---

### Post by LoneWolfJack on 2010-05-09
here's a small code snippet that will strip the magic quotes from within your script.

```

$_GET = strip_magic_quotes($_GET);
$_POST = strip_magic_quotes($_POST);


	function strip_magic_quotes($arr)

		{

		foreach($arr as $k=>$v)

			{

			if(is_array($v))

				{$arr[$k] = strip_magic_quotes($v);}

			else

				{$arr[$k] = stripslashes($v);}

			}

		return $arr;

		}

```

other than that, you could also configure this through apache virtual hosts.

---

