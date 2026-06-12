---
title: "how to access locked folder"
date: 2009-06-30
forum: General Help
---

### Post by jeremyjjbrown on 2009-06-30
I used photorec to recover photos of my trip to Europe from a crashed flash card. It seams to have recovered my photos but it saves them to a folder with a lock and red x on it. I'm thinking these folders are only accessable to root. Can anyone tell me how to unlock this folder so I can have my pix.

Thanks

---

### Post by credobyte on 2009-06-30
```
sudo chown -R user:user /path_to_photos

```
Replace user:user with your username ( eg. credobyte:credobyte ) and /path_to_photos with an actual path of your recovered pictures.

---

### Post by Boondoklife on 2009-06-30
> **jeremyjjbrown said:**
> I used photorec to recover photos of my trip to Europe from a crashed flash card. It seams to have recovered my photos but it saves them to a folder with a lock and red x on it. I'm thinking these folders are only accessable to root. Can anyone tell me how to unlock this folder so I can have my pix.

Thanks


If it is accessible by root then you can change the permissions by running `gksu nautilus`

This will open a nautilus window with root prvilages, then just browse to the files, right click and change the owner to your user.

---

### Post by jeremyjjbrown on 2009-06-30
Worked great, Thanks

My girlfriend will be very happy to see our pictures.

---

### Post by DeMus on 2009-06-30
> **jeremyjjbrown said:**
> I used photorec to recover photos of my trip to Europe from a crashed flash card. It seams to have recovered my photos but it saves them to a folder with a lock and red x on it. I'm thinking these folders are only accessable to root. Can anyone tell me how to unlock this folder so I can have my pix.

Thanks

Open a terminal ( Applications > Accessories > Terminal)
Type:
```
mkdir flashcard
```
```
cd flashcard
```
```
cp /path/to/present-location-of pictures/* .
```
```
cd ..
```
```
chmod -R 755 flashcard
```
This will create a folder flashcard and access it. Then all that is placed in the present location folder of your pictures will be copied to this new folder. **Change "/path/to/present-location-of pictures/" to whatever folder name you are using now.**
Next you will jump one folder up the tree and change the file mode bits so you should be able to access them.

---

