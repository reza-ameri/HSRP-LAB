Scenario: Setting Up an Internal DNS Server for the lab.local Domain with External Resolution Capability
In this scenario, I set up an internal DNS server responsible for managing the lab.local domain, while also ensuring that the server has access to the internet and can resolve external domains. This means that the server can resolve both internal network domain names (like pc1.lab.local) and external domains from the internet.

Steps Taken:
Setting Up the DNS Server: First, I set up an internal DNS server on a Linux system using BIND9, one of the most popular and widely used DNS software. The DNS server was configured to manage the lab.local domain for the internal network.

Configuring the Domain in named.conf: In the named.conf configuration file, I configured the lab.local domain exclusively for the internal network. This ensures that devices within the network can resolve local hostnames like pc1.lab.local, pc2.lab.local, and others, without needing to use IP addresses.

Allowing External DNS Resolution: To allow the DNS server to resolve external domains, I configured forwarders in the named.conf file. This means the server forwards DNS queries it can't resolve locally (such as google.com or other internet domains) to external DNS servers like Google's DNS (8.8.8.8).

Example configuration for forwarders:

bash
Copy
Edit


forwarders {
    8.8.8.8;  # Google DNS server
};


Testing the DNS Server: After configuring the server, I tested it using a Windows 7 machine. The Windows 7 machine was set to use the internal DNS server for resolving both lab.local domain names and external domains. I verified that:

The DNS server successfully resolved local network names like pc1.lab.local.
The DNS server also resolved external domains like google.com by forwarding the queries to external DNS servers.
With this configuration, I was able to set up an internal DNS server that supports resolving both internal domain names and external domains, providing seamless access to both internal and external resources.
![Image DNS Server](../../Image/image DNS Server.png)
