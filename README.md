# Create the table to import file:

CREATE table ust(
u_id int not null PRIMARY KEY,
i_id int null,
C_id int null,
Bh   varchar(10) null,
ts  char(20) null
)

# load file:

load data local infile "E:\\test\\UserBehavior1.csv"
into table ust
FIELDS terminated by ","
lines terminated by "\n"；

# change the fromat of timestamp which is integer to datetime and divide them into two columns
ALTER TABLE usertest ADD hr char(20);
UPDATE usertest SET hr=ts;
UPDATE usertest SET ts=FROM_UNIXTIME(ts,'%Y-%m-%d');
UPDATE usertest SET hr=FROM_UNIXTIME(hr,'%H');

# Funnel model to customer
