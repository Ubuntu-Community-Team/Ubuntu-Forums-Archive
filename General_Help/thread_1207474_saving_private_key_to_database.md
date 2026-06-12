---
title: "saving private key to database"
date: 2009-07-08
forum: General Help
---

### Post by xiaomahe on 2009-07-08
Hi, i have generated public and private key using
// Create the keypair
	$res=openssl_pkey_new();

	// Get private key
	openssl_pkey_export($res, $privatekey);

	// Get public key
	$publickey=openssl_pkey_get_details($res);
	$publickey=$publickey["key"];

i tried to save it into mysql database using varchar as the type with length 500..

When i saved it, it could not save the keys, hence dropping the value and in the end, my table is empty.

---

