# Introdução

Repositório criado durante a prática de map-matching utilizando a ferramenta [FMM](https://github.com/cyang-kth/fmm)

## Requerimentos

- Docker

## Como utilizar

### Primeiros passos

- Clone o repositório atual através da ferramenta `git clone`
- Entre no repositório clonado com `cd ./pratica-mapmatching`
- Crie um container docker através da [imagem](https://hub.docker.com/r/hqzqaq/fmm) disponibilizada
  - `docker run --mount type=bind,source="$(pwd)",target=/app -it --rm hqzqaq/fmm:1.0 bash`
    - Recomendamos a criaçãode um volume para armazenar os arquivos utilizados e gerados pelo algoritmo

### Configurando os dados

Para utilizar o algoritmo é necessário baixar a geometria do local de onde os dados se referem. Recomendamos a leitura deste [tutorial](https://github.com/cyang-kth/osm_mapmatching) para download dos arquivos shapefile necessários.


### Execução do map matching

Para conferir os comandos, argumentos e demais configurações, recomendamos a leitura da [wiki do FMM](https://fmm-wiki.github.io/) e visualização dos exemplos disponibilizados.

**Exemplo**

- FMM:

```sh
ubodt_gen --network /app/curitiba/edges.shp --network_id fid --source u --target v --output /app/curitiba/ubodt.txt --delta 0.03 --use_omp
```

```sh
fmm --ubodt /app/curitiba/ubodt.txt --network /app/curitiba/edges.shp --network_id fid  --source u --target v --gps /app/curitiba/selected.csv --gps_point -k 4 -r 0.4 -e 0.5 --output /app/curitiba/output.txt --use_omp
```

- STMatch
  
```sh
stmatch --network /app/curitiba/edges.shp --network_id fid  --source u --target v --gps /app/curitiba/selected.csv --gps_point -k 4 -r 0.4 -e 0.5 --output /app/curitiba/mr.txt
```

## Referências

- [Map matching on OpenStreetMap, a practical tutorial](https://github.com/cyang-kth/osm_mapmatching)
- [Fast map matching](https://fmm-wiki.github.io/)