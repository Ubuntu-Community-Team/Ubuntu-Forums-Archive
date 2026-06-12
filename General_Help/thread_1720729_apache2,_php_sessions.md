---
title: "apache2, php sessions"
date: 2011-04-03
forum: General Help
---

### Post by flandercan on 2011-04-03
Hi, 

I have an ubuntu 8.04 server running a couple of web sites using virtual hosts , apache2, mysql and php.

I have noticed that by default php sessions are created in /var/lib/php5 and all stored in plain text.

I have quickly created a php script in a separate virtual host to list and display all contents in /var/lib/php5 , and it seems incredibly easy to see what details the other accounts are storing in sessions. 

Is this the norm or should i be doing something to stop this?


Thanks 
Paul

---

### Post by SeijiSensei on 2011-04-03
Usually the sessions are kept in a directory owned by the Apache user with 0700 permissions.  Obviously if you run another PHP script, it will have access to this directory since it will also be running as the www-data user.  Other users on the machine (except root, of course) won't have any access to the stored sessions.

If you're really concerned about this, you could encrypt the data before saving it in the session.  Put the sensitive data in an array, use serialize() to create a string version of the array, then use the various mcrypt functions to encode it.  Stash the encrypted serialized data into the $_SESSION global array as a string.

I usually apply BASE64 ("MIME") encoding to the encrypted data to convert the encrypted binary to a plain-text string.  Here's a simple function I wrote to do encryption with AES256 (aka "rijndael-256"):

```

function b64_encrypt($string,$key) {

   # encrypt a string with Rijndael-256 and $key
   # return the base64 encoding of the encrypted result

   # from the PHP manual
   $td = mcrypt_module_open('rijndael-256', '', 'ecb', '');
   $iv = mcrypt_create_iv (mcrypt_enc_get_iv_size($td), MCRYPT_RAND);
   mcrypt_generic_init($td, $key, $iv);

   # base64 encode the result
   $encrypted_data = base64_encode(mcrypt_generic($td, $string));

   mcrypt_generic_deinit($td);
   mcrypt_module_close($td);

   return $encrypted_data;

}

```

The equivalent decryption function uses mdecrypt_generic() instead of mcrypt_generic().

Serialize the sensitive data array first, then hand it to this function for encryption.  Generate a strong key using a SHA1 hash like this from the command prompt:

```
ps auxw | grep sha1sum
```

You'll get a 32-byte hash string based on the machine's current process table.  Ignore the trailing hyphen after the hash.  You'll have to put the key in a file somewhere where only the www-data user can read it, so make sure it's owned by that user with 0600 permissions.  Do not put it in /var/www, but in some other uncommon location.

---

