###[7] create table contact (fnmae,lname,contact,email,city) perform following

##1.insert contact 8 records

##2.delete contact


```python
 import sqlite3 as sq
```

#connect to the py.db database


```python
conn=sq.connect("C:\\23bca259\\sqlite3\\csv\\py.db")
```


```python
cur=conn.cursor()
```

#create table contact


```python
cur.execute('''
    create table if not exists contact(
          fname text,
          lname text,
          contact text,
          email text,
          city text
         )
      ''')   
```




    <sqlite3.Cursor at 0x1b7ec63d540>



#insert 8 records in the table


```python
records = [
        ('om','patel','9725638716','om@gmail.com','surat'),
        ('sai','raval','1234567890','sai@gmail.com','karchelia'),
        ('ram','raval','9898929716','ram@gmail.com','surat'),
        ('sujal','vadhiya','9725630716','sujal@gmail.com','navsari'),
        ('meet','vadhiya','2192725960','meet@mail.com','surat'),
        ('rahul','joshi','1234567890','rahul@mail.com','bardoli'),
        ('vicky','doshi','5432156780','vicky@gmail.com','vankaner'),
        ('kaushik','raval','9725639716','kaushik@gmail.com','bhavangr'),
         ] 
      
```

#execute insert query


```python
cur.executemany('''
insert into contact(fname, lname, contact,   email,city)
values(?,?,?,?,?)
''', records)
```




    <sqlite3.Cursor at 0x1b7ec63d540>




```python
conn.commit()
```

#create trigger


```python
cur.execute('''
create trigger if not exists delet_trigger
before delete on contact
for each row
when old.fname = 'ram'
   begin
        delete from contact where fname ='ram';
     end;
     ''')
```




    <sqlite3.Cursor at 0x1b7ec63d540>




```python
conn.commit()
```


```python

```
