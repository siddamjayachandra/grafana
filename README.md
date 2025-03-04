# Set Up Application Monitoring with Prometheus & Grafana

1. First install the docker and docker-compose in your instance.

2. Now configure the docker compose file to pull the images of grafana, prometheus and node exporter applcation.

3. Configure the yaml file for linking up the promethues with the application in our case it is node exporter applictaion.

4. Both docker-compose and prometheus yaml files are present in this repository go through it.

5. Run the docker compose command to build the images.
 "docker-compose up -d".   

6. Check the images by using "docker ps". It shows the images of grafana, prometheus and node exporter application images along with the port numbers.

7. Access the grafana UI using your server IP and port number. once you see the UI page login with admin as a username and setup the password.

8. In the grafana menu bar go to the connections and select the data sources.

9. Now create a new data source and select the prometheus which is default. and in the connection give the url of prometheus along with port number. usally it will be your server ip and port number can be seen in the images list. Save the data source.

10. In the menu bar go to dashboards and create a new dashboard. Select the add visualization. It asks for the data source selcet the prometheus.

11. Now write the query in the query inspector. Select code to write the query. If you want to see the cpu usage paste this query "100 - (avg by (instance) (rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)".

12. Add query and if you want to write the query for the memeory usage, use this code for memory "node_memory_Active_bytes / node_memory_MemTotal_bytes * 100".

13. Run the qureies and now observe the dash board you can see the graph representing the usages of memory and cpu.

14. If you want to manually test the usgae of cpu and memoery install the stress-ng. And run stress on cpu and memory.
commands are "stress-ng --vm 4 --vm-bytes 1G --timeout 60s" and "stress-ng --cpu 0 --cpu-method matrixprod". You can replace the number of cpu and vm you want.

15. After running these commands and when you run the query in the grafana dashboard. The graph show the usages of cpu and memory.

16. This is my output of the grafana dashboard.

![image](https://github.com/user-attachments/assets/86d10e30-efff-4a17-bf3f-80c18315424d)


 
