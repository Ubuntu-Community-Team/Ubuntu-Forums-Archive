---
title: "Mono 2.10.2 on Ubuntu 11.04"
date: 2011-07-15
forum: General Help
---

### Post by JHorrocks on 2011-07-15
This is a previous post I posted over 1 month ago on mono-project website (to my stupid mistake... didnt realise after waiting 1 month for a response that they wont reply as they dont support ubuntu!)

If anyone would be able to give any guidance, it would be greatly recieved..

--------------------------------------------------------------------

                                            I have ported over from windows server **to** **mono** 2.10.2 on my dev server running on ubuntu 11.04 and I have 1 issue regarding serialization.

In my original **code** running windows IIS I save a user **object** into mysql as datatype blob 

example: 
sqlCommand.Parameters.Add("pin_user_object", MySqlDbType.**Blob**).Value = XXX.Library.UtilitiesLayer.**ObjectToByteArray**(oUserObjects); 

Then I use 2 methods **to** serialize/deserialize when inserting or retrieving the record: 

example: 
// **Convert** an **object** **to** a byte array 

        public static byte[] **ObjectToByteArray**(**Object** obj) 

        { 

            if (obj == null) 

                return null; 



            BinaryFormatter bf = new BinaryFormatter(); 

            MemoryStream ms = new MemoryStream(); 



            bf.Serialize(ms, obj); 



            return ms.**ToArray**(); 

        } 



        // **Convert** a byte array **to** an **Object** 

        public static **Object** ByteArrayToObject(byte[] arrBytes) 

        { 

            MemoryStream memStream = new MemoryStream(); 

            BinaryFormatter binForm = new BinaryFormatter(); 



            memStream.Write(arrBytes, 0, arrBytes.Length); 

            memStream.Seek(0, SeekOrigin.Begin); 



            **Object** obj = (**Object**)binForm.Deserialize(memStream); 



            return obj; 

        } 

Now the error that is being thrown **to**  me is "this feature isn't implemented". From what I understand it is  the Serialize(); and Deserialize methods that is not implemented yet. 

So my question is, **can** I rewrite the above 2 methods into something that allows me **to** save the user **object** as a **blob** that **mono** accepts? 

Regards, and thanks for any help in advance

---

