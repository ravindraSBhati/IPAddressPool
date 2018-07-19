# IPAddressPool

OVERVIEW: 
C# Wrapper for IPAddress ranges
This IPPoolhelper is designed to search IPAddress from a collection of IP Ranges(Currently supporting only IPV4). 

 
FEATURES:
It contains following features: 
 

It can search from a vast collection of IPV4 Ranges. 
It can search IP from a particular group of IP range collection. 
It can return Network Address from IPAddress and subnet mask. 
It can convert Decimal to CIDR. 
It can convert CIDR to Decimal too. 
It can check for two IPAddresses, if they are in same subnet mask. 

USES:
We need to follow below steps to load IP ranges. 

 public void BootstrapIPPoolWrapper() 
        { 
            //bootstarp the ip helper 

            //IPPoolWrapper.IPPoolHelper.Initialize("IpList.json","idea"); 
            IPPoolHelper.Initialize(new Dictionary<string, string>() 
            { 
                { "region1","test1.json"}, 
                { "region2","test2.json"}, 
                { "region3","test3.json"} 
            }); 
        } 

 

As we can see in above example we can divide IP Range collection to different regions. 
In above code sample all 3 files contain different ip pool ranges stored in json format.  

test1.json 

[	 
"41.48.0.0/13", 
"41.48.0.0/14", 
"41.50.0.0/16", 
"41.52.0.0/14", 
"41.156.0.0/15", 
"41.156.0.0/16", 
"41.156.1.0/24", 
"41.156.64.0/19", 
"41.156.64.0/20", 
"41.156.80.0/20", 
"41.157.0.0/16", 
"41.157.64.0/18", 
"41.157.64.0/19", 
"41.157.96.0/19", 
"197.104.0.0/13", 
"197.104.0.0/14", 
"197.108.0.0/14", 
"197.168.0.0/13", 
"197.168.0.0/14", 
"197.172.0.0/14", 
"105.0.0.0/12" 

] 


test2.json 
[ 
"41.208.48.0/23", 
"41.208.50.0/24", 
"41.208.11.0/24" 
] 

 

For searching a particular IP we will follow step. 

bool result = IPPoolHelper.Current.IsExists("41.157.0.128");  


If we knew about the group that contains the IP, we can simply call the IsExists with the group name as below,  

bool result = IPPoolHelper.Current.IsExists(IPAddress.Parse("41.157.0.128"), "region1"); 

 

The results will be return as boolean value, if ip exists then True otherwise False will be returned.
We can easily get list of Iprange groups with following step.  

IList<string> regions = IPPoolHelper.Current.RegionKeys; 
 

We can also get region from ip by following step. 

String region = GetRegion(iPAddress); 

 

 
