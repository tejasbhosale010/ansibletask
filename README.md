1. Setup password less ssh access for user which you want to run this code (I used ansible user , ansible is having sudo access)
2. To generate key on ansible tower login to user and use ssh-keygen
3. After that copy key to remote node using ssh-copy-id username@ip
4. Used two node for this setup
  4.1 grafana node where grafana and promethus is installed
  4.2 To run this code on grafana node update hosts file with private ip
  4.3 ansible-playbook -K grafana-config.yaml  
5. Node whose nginx and node metric we want to monitor for this i used local ansible tower
  5.1 ansible-playbook -K node_exporter.yaml 
6. Login to grafana publicip:3000 with default username admin and password admin
7. Add datasource as promethus as default datasource
  7.1 Click Connections in the left-side menu.
  7.2 Under Your connections, click Data sourcesi add new datasource.
  7.3 Select prometheus add connection url : http://127.0.0.1:9090 , no authentication after that save and test it.

8. Regarding dashboards there are multiple read made dashboard available so i used those imported in grafana
  8.1 https://github.com/nginxinc/nginx-prometheus-exporter
  8.2 https://grafana.com/grafana/dashboards/1860-node-exporter-full/

9. Can access those grafana

  9.1 http://13.127.229.181:3000/dashboards
  9.2 username admin
  9.3 password  Tejas@123
