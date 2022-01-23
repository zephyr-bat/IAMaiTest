# IAMainTestGUILLERMELEBRETON

## Installation
(Nécessite python V3.6)

Télécharger le git

Dans le dossier téléchargé, dans le CMD taper la commande: 
py -3.6 -m venv temp
pour créer un dossier d'environnement virtuel pour python.

Utiliser cette commande pour activer les scripts
temp\Scripts\activate
Utiliser cette commande pour Installer les requirements
pip install -r requirements.txt

Mettre les poids d’entrainements dans le dossier data

# Flux vidéo
Transforme les poids en poids tensortflow
python save_model.py --weights ./data/yolo-obj_final.weights --output ./checkpoints/WeightTensortflow-416 --input_size 416 --model yolov4

Lance l'analyse du flux vidéo 
python detect_video.py --weights ./checkpoints/ WeightTensortflow-416 --size 416 --model yolov4 --video 0 --output ./detections/results.avi

# Evaluation cocotools

Dans le CMD /dossier téléchargé/scripts

Indique quelles annotations utiliser.
python coco_convert.py --input ./dossierEvaluation/_annotations.coco.json --output examTest.pkl

Indique le chemin des annotation pour cocotools
python coco_annotation.py --coco_path ./

Dans le dossier téléchargé lancer 
python evaluate.py

Dans le dossier mAP/extra lancer
python remove_space.py

Pour lancer l'évaluation, retour dans le dossier principal taper
python main.py --output results_yolov4_tf
