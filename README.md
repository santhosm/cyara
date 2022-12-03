# Cloud Agnostic Deployment

## Strategies:
These are the strategies and tools used to implement cloud agnostic design
 -  **Containerization**
Containerization is supported by all major cloud providers and they can be implemented in on premise DC as well. Containerization solves lock step in deployment process, bin packing. Easy rollback and redeployment of service can be achieved by using kubernetes deployment object. **Managed Kubernetes clusters** come in handy. It assists you in orchestrating your microservices containers and is managed so updates and HA are taken care of
-  **Monitoring and service availability**
open-source monitoring tools which can be easily integrated on all major clouds. **Prometheus** is used for monitoring and alerting, along with **Grafana** for dashboarding. This provides API, CLI, and WebUI to monitor the status of the services
 - **IAC**
 Though cloud providers provide their own template better option would be to use **Terraform** to achieve cloud agnostic 
## Design diagram


## Highlevel kube definition 
- **Deployment configuration**
		Runtime configuration of the deployments can be mounted as config file rather than using ansible or chef  in deployment definition this provides convenient way for developers to specify the run configuration for their service
``` yaml
volumes:
	- name: configfile
	  configMap:
      name: configfile
```
``` yaml
volumeMounts:
- name: script
  mountPath: "/etc/cyara/configfile"
```

- **Service configuration**
	- For service that are to be exposed outside of the cluster we expose it via ingress controller (UI) (deployment -> service -> ingress)
	- For service that are not exposed outside cluster they are exposed via service  (deployment ->service)
	- the connection between the services will be based on kube dns ({service}.{namespace}.svc.cluster.local
- **POC**
	- https://github.com/santhosm/santhos-media 
	
	
 
 
 
